# 아이템1. Enum
1. **열거 타입**은 인스턴스가 하나만 만들어짐을 보장한다. - Enum (p9)
   - 상수 목록을 담을 수 있는 데이터 타입
   - 특정한 변수가 가질 수 있는 값을 제한 할 수 있다. **타입-세이프티**를 보장할 수 있다.
   - **싱글톤 패턴**을 구현할 때 사용하기도 한다.
   > 질문 1) 특정 enum 타입이 가질 수 있는 모든 값을 순회하며 출력하라.
Arrays.stream(OrderStatus.values()).forEach(System.out::println);

    > 질문 2) enum은 자바의 클래스처럼 생성자, 메소드, 필드를 가질 수 있는가?
    네

    > 질문 3) enum의 값은 == 연산자로 동일성을 비교할 수 있는가?
네 오히려 equals를 사용하면 NullPointerException이 발생할 수 있음. <br>
   if(order.orderStatus.equals(OrderStatus.DELIVERED)) //이때

   > 질문 4) enum을 key로 사용하는 Map을 정의하시오. 또는 enum을 담고 있는 Set을 만들어 보세요.
HashMap, HashSet 보다 EnumMap이랑 EnumSet을 사용하면 좋다.
   
    ### EnumMap
    열거형 상수를 Key로 사용하는 Map의 구현체입니다. 
    열거형 상수 값을 Key로 사용할 수 있으며, 각 상수마다 고유한 value를 매핑하여 사용할 수 있습니다. 
    EnumMap은 내부적으로 배열로 구현되어 있어서 매우 빠른 성능을 제공하며, 다른 Map에 비해 메모리 사용량이 적습니다.
    > hashmap 은 key를 bucket에 저장하고각 bucket이 linked list를 참조 하고 있음.
    (linkedlist에는 hash(key)가 같은 element가 들어감) 그런데 enummap 의 경우 key로 사용할 값이 제한되어 있으므로, 그 갯수만큼 길이를 가진 array를 선언하고. 해당 index에 값을 넣으면 됨.

    ### EnumSet
    EnumSet은 열거형 상수를 사용하여 집합(Set)을 구현하는 클래스입니다. 
    Set의 특성상 중복된 원소를 허용하지 않으며, 내부적으로 비트 벡터로 구현되어 있어서 매우 효율적이고 작은 메모리를 사용합니다. 
    EnumSet은 비트 연산을 통해 집합 연산을 매우 빠르게 수행할 수 있습니다. 
    > hashset은 hashmap 과 같은데 map의 value가 있다 없다를 표현하는 지시자 같은 값이 들어감. 
   > enumset은 값이 있다 없다만 표시하면 되니까 enummap 처럼 array로 구현하지 않고 10101011 같은 bitvector로 구현이 가능.

2. 같은 객체가 자주 요청되는 상황이라면 **플라이웨이트 패턴**을 사용할 수 있다. (p9)
3. 자바8부터는 **인터페이스가 정적 메서드**를 가질 수 없다는 제한이 풀렸기 때문에 인스턴스화 불가 동반 클래스를 둘 이유가 별로 없다. (p10)
4. **서비스 제공자 프레임워크**를 만드는 근간이 된다. -Spring (p11)
5. **서비스 제공자 프레임워크**가 없다면 각 구현체를 인터페이스로 만들 때 리플렉션을 사용해야한다. (p12)
6. 브리지 패턴 (p12)
7. 의존 객체 주입 프레임워크 (p12)