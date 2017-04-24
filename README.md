#### 1. Tomcat 서버를 시작할 때 웹 애플리케이션이 초기화하는 과정을 설명하라.
* web application이 초기화를 시작하면 servlet context event가 발생하여 servlet-context-listener가 해당 event를 읽는다
* 해당 servlet-context-listener에서 초기화 하는 콜백함수를 호출한다.
* db를 초기화 하기위해 jwp.sql파일을 읽어 sql문을 실행시킨다.
* 

#### 2. Tomcat 서버를 시작한 후 http://localhost:8080으로 접근시 호출 순서 및 흐름을 설명하라.
* 

#### 7. next.web.qna package의 ShowController는 멀티 쓰레드 상황에서 문제가 발생하는 이유에 대해 설명하라.
* 
