#### 1. Tomcat 서버를 시작할 때 웹 애플리케이션이 초기화하는 과정을 설명하라.
* web application이 초기화를 시작하면 servlet context event가 발생하여 servlet-context-listener가 해당 event를 읽는다
* 해당 servlet-context-listener에서 초기화 하는 콜백함수를 호출한다.
* db를 초기화 하기위해 jwp.sql파일을 읽어 sql문을 실행시킨다.
* Dispatcher Servlet을 WebServlet으로 등록할 때 loadOnStartUp=1 옵션을 주어 WebServlet이 생성되는 시점에 초기화를 진행한다.
* Dispatcher Servlet의 init함수가 호출되어 RequestMapping 클래스가 생성되고 RequestMapping 클래스의 initMapping 함수가 호출되어 해당되는 uri로 Controller가 맵핑된다.

#### 2. Tomcat 서버를 시작한 후 http://localhost:8080으로 접근시 호출 순서 및 흐름을 설명하라.
* DisPatcher Servlet에서 uri를 분석하여 request-mapping으로 부터 해당되는 controller를 가져온다.
* http://localhost:8080의 경우 요청 uri가 "/" 이므로 HomeController가 맵핑된다.
* HomeController의 service에서 ModelAndView 타입으로 return하는데 Model 에 questionDao.findAll이 들어간 상태로 View인 jspView를 호출한다.
* jspView는 home.jsp view와 model을 맵핑하여 html을 응답한다.

#### 7. next.web.qna package의 ShowController는 멀티 쓰레드 상황에서 문제가 발생하는 이유에 대해 설명하라.
* ShowController의 execute method 밖에서 data에 접근하게 되면 single instance인 controller에 접근한 data가 멀티 쓰레드에서 같은 곳을 바라보게 된다.
* 멀티 쓰레드가 동시에 한 data를 바라보게 되면 기존 쓰레드가 접근 했던 data가 다음에 접근하는 쓰레드에 의해 레퍼런스가 변경될 가능성이 있다.
