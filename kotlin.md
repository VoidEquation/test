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
