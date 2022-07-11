### Web Server VS Web Application Server

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
# 웹 서버
 - 하드웨어와 소프트웨어로 구분됨
   - 하드웨어 : Web 서버가 설치된 컴퓨터
   - 소프트웨어 : 웹 브라우저 클라이언트로부터 HTTP 요청을 받고, 정적인 컨텐츠를 제공하는 프로그램

웹 서버 기능
 - HTTP 프로토콜을 기반으로, 클라이언트의 요청을 서비스하는 기능을 담당
 - 정적 컨텐츠 제공
   - WAS를 거지치 않고 바로 자원 제공
 - 동적 컨텐츠 제공을 위한 요청 전달
   - 클라이언트 요청을 WAS에 보내고, WAS에서 처리한 결과를 클라이언트에게 전달
