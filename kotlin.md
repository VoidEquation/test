# 코틀린 개발 삽질기록

## JPA
### JPA Native Query
* JPA Native Query로 count()를 하면 리턴타입이 BigInteger 로 됨
* 해당 데이터를 가공 처리할 때, 코틀린 기본타입으로 변환이 필요함.
* ex) Long 타입으로 변경할 경우 .toLong() 을 사용해야함
* 다른 Map 등 구조에 넣을 경우, nullable이기 때문에 !!.toLong() 을 사용해서 타입변환을 해야함
### findBy Nullable
* findBy에서 아무값도 못 찾을 경우가 있다면 리턴 타입을 nullable 하게 선언해야 함
* 아니면 실행하는데 이상이 없어도 에러가 발생함

## Collection
### mutable
* 변경가능한 컬렉션 타입을 사용하려면 mutable~~ 로 시작하는 선언문을 사용해야 한다.
* ex) mutableListOf<Long>, ListOf<Long>

## enum / when
### when 식의 인자로 아무 객체나 사용가능
```kotlin
fun mix(c1: Color, c2:Color) = 
  when (setOf(c1, c2)) {
    setOf(RED, YELLOW) -> ORANGE
    setOf(YELLOW, BLUE) -> GREEN
    setOf(BLUE, VIOLET) -> INDIGO
    else -> throw Exception("Dirty color")
 }
```

### map
* get과 put을 사용하는 대신 map[key]나 map[key] = value를 사용해 값을 가져오고 설정할 수 있다
```kotlin
binaryReps[c] = binary
binaryReps.put(c, binary)
```

### list
* 인덱스와 함께 컬렉션을 이터레이션 할 수 있음
```kotlin
var list = arrayListOf("10", "11", "1001")
for ((index, element) in list.withIndex()) {
  println("$index: $element")
}
```

### to
* 코틀린에서 to라는 단어는 키워드가 아님
* 이 코드는 중위 호출(infix call)이라는 특별한 방식으로 to라는 일반 메소드를 호출한 것
* 중위 호출 시에는 수신 객체와 유일한 메소드 인자 사이에 메소드 이름을 넣음
```kotlin
// 동일
to("one")
to "one"
```
to 함수 정의
```kotlin
infix fun Any.to(other: Any) = Pair(this, other)
```

### property
* lateinit : 변경자를 null이 될 수 없는 프로퍼티에 지정하면 프로퍼티를 생성자가 호출된 다음에 초기화
* lazy initialized(지연 초기화) : 요청이 들어오면 비로소 초기화 됨. 더 일반적인 위임 프로퍼티의 일종

### 멤버 참조 
* ::를 사용하는 식을 멤버 참조(member reference)라고 부름
* ::는 클래스 이름과 참조하려는 멤버(프로퍼티나 메소드) 이름 사이에 위치

### with 함수
* 어떤 객체의 이름을 반복하지 않고도 그 객체에 대해 다양한 연산을 수행하는데 사용
* with 함수는 첫 번째 인자로 받은 객체를 두 번째 인자로 받은 람다의 수신 객체로 만든다
* with가 반환하는 값은 람다 코드를 실행한 결과

### apply 함수
* with와 비슷하나 차이는 apply는 항상 자신에게 전달된 객체를 반환한다는 점임
* apply는 확장 함수로 정의됨
