# Web Server VS Web Application Server

정적 페이지 vs 동적 페이지

정적 페이지(Static Pages)
 - 바뀌지 않는 페이지
 - 웹 서버는 파일 경로 이름을 받고, 경로와 일치하는 file contents를 반환
 - 항상 #동일한 페이지를 반환

동적 페이지(Dynamic Pages)
 - 인자에 따라 바뀌는 페이지
 - 웹 서버에 의해 실행되는 프로그램을 통해 만들어진 결과물
 - 개발자는 Sevlet에 doGet() 메소드를 구현함

![was vs web server](https://gmlwjd9405.github.io/images/web/webserver-vs-was1.png)
### 웹 서버
 - 하드웨어와 소프트웨어로 구분됨
   - 하드웨어 : Web 서버가 설치된 컴퓨터
   - 소프트웨어 : 웹 브라우저 클라이언트로부터 HTTP 요청을 받고, 정적인 컨텐츠를 제공하는 프로그램

웹 서버 기능
 - HTTP 프로토콜을 기반으로, 클라이언트의 요청을 서비스하는 기능을 담당
 - 정적 컨텐츠 제공
   - WAS를 거지치 않고 바로 자원 제공
 - 동적 컨텐츠 제공을 위한 요청 전달
   - 클라이언트 요청을 WAS에 보내고, WAS에서 처리한 결과를 클라이언트에게 전달

### WAS(Web Application Server)
 - DB 조회 및 다양한 로직 처리 요구시 동적인 컨테츠를 제공하기 위해 만들어진 애플리케이션 서버
 - HTTP를 통해 애플리케이션을 수행하는 미들웨어
 - 웹 컨테이너 or 서블릿 컨테이너라고 불림
 - WAS = 웹 서버 + 웹 컨테이너
 - 웹 서버의 기능들을 구조적으로 분리하여 처리하는 역할

WAS 주요 기능
 - 프로그램 실행 환경 및 DB 접속 기능 제공
 - 여러 트랜잭션 관리 기능
 - 업무 처리하는 비즈니스 로직 수행

### 둘을 구분하는 이유
웹 서버가 필요한 이유
 - 정적 컨텐츠만 처리하도록 기능 분배를 해서 서버 부담을 줄임

WAS가 필요한 이유
 - 요청에 맞는 데이터를 DB에서 가져와 비즈니스 로직에 맞게 그떄마다 결과를 만들고 제공하면 자원을 효율적으로 사용할 수 있음

WAS로 웹 서버 역할을 다 처리할 수 있는데 안하는 이유
 - WAS가 웹서버의 정적 컨텐츠 요청까지 처리하면, 부하가 커지고 동적 컨텐츠 처리가 지연되면서 속도가 느려짐

### 가장 효율적인 방법
![효율적인 방법](https://gmlwjd9405.github.io/images/web/web-service-architecture.png)
 - 웹 서버를 WAS 앞에 두고, 필요한 WAS들을 웹서버에 플러그인 형태로 설정하면 효율적인 분산 처리가 가능함

순서
 - 클라이언트의 요청을 웹 서버가 먼저 받은 다음, WAS에 보내 관련도니 Servlet을 메모리에 올림
 - WAS는 web.xml을 참조해 해당 Servlet에 대한 스레드 생성
 - 이때 HttpServletRequest와 HttpServletResponse 객체를 생성해 Servlet에게 전달
 - doGet()이나 doPost()메소드는 인자에 맞게 생성된 적절한 동적 페이지를 Response 객체에 담아 WAS에 전달
 - WAS는 Response 객체를 HttpResponse 형태로 바꿔 웹 서버로 전달
 - 생성된 스레드를 종료하고, HttpServletRequest와 HttpServletResponse 객체 제거

