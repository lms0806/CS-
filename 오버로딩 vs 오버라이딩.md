오버로딩(Overloading)
 - 같은 메소드라도 매개변수만 다르면 얼마든지 정의하고 사용 가능

특징
 - 메소드 이름이 같아야함
 - 리턴형이 같아도 되고, 달라도 됨
 - 파라미터 개수가 달라야함
 - 파라미터 개수가 같을 경우, 데이터타입이 달라야함

overridng 내부 구현 방식에는 name mangling이 있는데, 해당 방식은 c++에서만 사용이 가능함
java는 각 메서드에 메소드 설명자를 추가하여 찾음 


오버라이딩(Overriding)
 - 상속 관계에 있는 클래스 같에 같음 이름의 메소드를 정의하는 기술
 - 자식 클래스가 부모 클래스에서 선언된 것과 같은 메소드를 가질 때, 메소드 오버라이딩이라 함

특징
 - 오버라이드 하고자 하는 메소드가 상위 클래스에 존재해야함
 - 메소드 이름이 같아야함
 - 메소드 파라미터 개수, 파라미터의 자료형이 같아야함
 - 메소드 리턴형이 같아야함
 - 상위 메소드와 동일하거나, 내용이 추가되어야함

오버라이딩은 vtable 라는 테이블을 이용하여 하고, vtable은 자신으로부터 Object 까지의 모든 조상들까지 정의된 메소드를 전부 가지는데, 자신을 포함해 가장 마지막으로 오버라이드된 코드를 가리킴
