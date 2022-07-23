# JPA란?

### JPA는 Java Persistence API다
 - 자바 영속성(데이터를 실행한 프로그램의 실행이 종료되더라도 사라지지 않는 데이터의 특성) API라는 의미 
 - 자바 프로그램에서 하드디스크(DBMS)에 기록하여 영구적으로 기록할 수 있는 환경을 제공하는 API
 - API(Applictaion Programming Interface)란?
   - 애플리케이션에서 데이터를 소통하기 위해 사용하는 인터페이스

### JPA는 ORM(Object Relational Mapping) 기술
 - 객체를 데이터베이스에 연결하는 방법론
 - 데이터베이스에 직접 테이블을 생성하지 않고, 인터페이스를 지켜서 자바의 객체를 이용하여 데이터베이스에 테이블이 생성되게 하는 기법
![JPA](https://www.saichoiblog.com/wp-content/uploads/2021/11/ORM.jpg)

### JPA는 반복적인 CRUD 작업을 생략하게 해줌
 - 데이터베이스의 데이터와 자바 객체 간의 반복적인 CRUD 작업을 함수로 제공해줌
 - JPA가 생략해주는 작업들
   - 자바 프로그램이 데이터베이스에 커넥션을 요청하면서 세션이 오픈됨
   - 자바 프로그램이 데이터베이스에 쿼리를 전송하여 데이터를 요청함
   - 자바 프로그램이 응답받은 데이터를 자바 객체로 변경함

### JPA는 영속성 컨텍스트(Persistence Context)를 가지고 있음
 - 영속성 컨텍스트는 자바에서 데이터베이스와의 모든 CRUD 작업을 관리하는 영역
 - 데이터의 CRUD가 일어나면 자동으로 동기화해줌
 - 자바 오브젝트 타입으로 변경하여 영구적으로 하드웨어에 기록함
![JPA -> DB](https://www.saichoiblog.com/wp-content/uploads/2021/11/Persistence-Context.jpg)

### JPA는 DB와 OOP의 불일치성을 해경하기 위한 방법론을 제공함
 - 자바와 달리 데이터베이스는 객체 저장 불가능하기 때문에 자바와 데이터베이스 간의 모순이 생기는데, JPA는 이 모순을 해결하기 위한 방법을 제공함
 - 객체 형태의 데이터를 스캔하게 되면 자동으로 FK를 생성하여 데이터베이스 칼럼을 만들어줌
![object -> db](https://www.saichoiblog.com/wp-content/uploads/2021/11/OOP-e1637809860758.jpg)

### JPA는 OOP의 관점에서 모델링을 할 수 있게 해줌
![obejct -> db, extends](https://www.saichoiblog.com/wp-content/uploads/2021/11/OOP-modeling.jpg)
