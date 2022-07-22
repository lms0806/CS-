# Spring boot 동작 원리

### (1) 서블릿 컨테이너
 - Http 요청을 받아 웹페이지를 동적으로 생성하는 역할
 - 대표적인 서블릿 컨테이너 : 톰캣(Tomcat)
 - 스프링 부트에는 톰캣이 내장되어 있음

### (2) web.xml
 - ServletContext의 초기 파라미터 설정
   - 초기 파라미터를 설정해 두면, 스프링의 모든 영역에서 권한과 인증을 체크하여 필터링 가능
 - 세션(Session)의 유효시간 설정
   - 권한과 인증이 완료된 사용자의 사용 가능 시간을 설정할 수 있음
 - Servlet/JSP에 대한 정의 및 매핑
   - 서블릿과 JSP를 검토하여 목적지에 도달할 수 있게 유도해줌
 - Mime Type 매핑
   - 스프링에 접근하는 데이터 타입을 확인하여 목적지의 타입으로 변경해줌
 - Welcome File List
   - 필터링 대상이 없는 데이터의 접근 시, 공통된 영역으로 보내주기 위한 파일을 가지고 있음
 - Error Pages 처리
   - 필터링 할 수 없는 데이터의 접근시, 에러 페이리로 보내줌
 - 리스너/필터 설정
   - 바쁜 업무를 대리해 주는 리스너와 사용자의 권한과 인증을 체크하거나 반입 금지 요소를 필터하는 설정가능
 - 보안
   - 프로그램에 위험한 영향을 줄 수 있는 사용자를 막아줌

### (3) DispatcherServlet
 - FrontController 패턴과 RequestDispacher 기능을 묶어서 제공함(디스패쳐 서블릿)
 - 직접 코드를 짜지 않아도 스프링에 기본 탑재되어 있음
 - 디스패쳐 서블릿과 함께 자동생성 되는 객체(IoC(제어의 역전))가 있는데, 그 중에 필터가 있다.
 - 기본적으로 필요한 필터가 제공되거나 개발자가 직접 등록할 수 있음
 - FrontController 패턴
   - web.xml의 일을 나누어서 하도록 만드는 패턴
   - 프론트 컨트롤러에서 자원에게 재요청 혹은 재응답을 하게 되는데 최초에 web.xml에게 한 요청/응답과 동일하게 유지할 수 있게 RequestDispatcher를 사용함
 - RequestDispathcer
   - FrontController에 도착한 요청/응답을 그대로 유지시켜줌
   - 페이지 이동시에 동일한 데이터를 가지고 이동할 수 있음

### (4) 스프링 컨테이너
 - ApplicationContext(Ioc 컨테이너)
   - 디스패쳐 서블릿에 의해 생성되는 객체
 - Ioc 컨테이너 순서
   - (1) 외부에서 요청이 들어옴
   - (2) web.xml을 거쳐 필터링됨
   - (3) ContextLoaderListener에서 DB 관련 공통 로직을 메모리에 띄움
   - (4) 디스패쳐 서블릿이 컴포넌트 스캔을 하여 메모리에 띄우고 주소 분배를 함
 - ApplicationContext의 종류
   - servlet-applicationContext
      - ViewResolver, Interceptor, MultipartResolver 객체를 생성하고 웹과 관련된 어노테이션 Controller, RestController를 스캔함
      - 해당 파일은 DispatcherServlet에 의해 실행됨
   - root-applicationContext
      - 해당 어노테이션을 제외한 어노테이션 Service, Repository 등을 스캔하고 DB 관련 객체를 생성함
      - 해당 파일은 ContextLoaderListener에 의해 실행됨
      - ContextLoaderListener를 실행해주는 녀석은 web.xml이기 때문에 root-applicationContext는 servlet-applicationContext보다 먼저 로드됨
 - Bean Factory
   - 필요할 때만 객체를 빈 팩토리에 등록하는 레이지 로딩이 됨

### (5) 컨트롤러 요청
 - 요청 주소에 따른 적절한 컨트롤러의 함수를 찾아서 실행함

### (6) 응답
 - 응답하는 방법
   - 파일 리턴
     - ViewResolver가 작동
   - 데이터 리턴
     - MessageConverter(@ResponseBody)가 작동
     - 메시지 컴버터는 오브젝트를 리턴할 때 json 타입으로 리턴함
![작동 순서](https://www.saichoiblog.com/wp-content/uploads/2021/11/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7-2021-11-26-%EC%98%A4%ED%9B%84-2.24.57-768x373.png)

※출처 : https://www.saichoiblog.com
