# Spring 용어 정리

### DI(Dependency Injection) 의존성 주입
 - Spring 프레임워크의 3가지 핵심 프로그래밍 모델 중 1가지
 - 외부에서 두 객체 간의 관계를 결정해주는 디자인 패턴
 - 인터페이스를 사이에 둬서 클래스 레벨에서는 의존관계가 고정되지 않도록 하고 런타임 시에 관계를 동적으로 주입
 - 필요한 이유
   - 두 객체 간의 관계라는 관심사의 분리
   - 두 객체 간의 결합도를 낮춤(결합도가 낮고, 유연성이 높아야 좋은 프로그램)
   - 객체의 유연성을 높임
   - 테스트 작성을 용이하게함
### AOP(Aspect Oriented Programming) 관점 지향 프로그래밍
 - 어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점으로 나누어서 보고 그 관점을 기준으로 각각 모듈화하겠다는 것
![AOP](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F994AA3335C1B8C9D28)
 - Aspect로 모듈화하고 핵심적인 비즈니스 로직에서 분리하여 재사용하겠다는 것
 - 주요 개념
   - Aspect : 흩어진 관심사를 모듈화 한것
   - Target : Aspect를 적용하는 곳(클래스, 매서드 등등)
   - Advice : 실직적으로 어떤 일을 해야할 지에 대한 것
   - JointPoint : Advice가 적용될 위치
   - PointCut : JoinPoint의 상세한 스펙을 정의한 것
 - 스프링 AOP 특징
   - 프록시 패턴 기반의 AOP 구현체
   - 스프링 빈에만 AOP 적용 가능
   - 모든 AOP의 기능을 제공하는 것이 아닌 스프링 Ioc(제어의 역전)와 연동하여 엔터프라이즈 애플리케이션에서 가장 흔한 문제에 대한 해결책을 지원하는 것이 목적

※ 출처 : https://engkimbs.tistory.com/746
