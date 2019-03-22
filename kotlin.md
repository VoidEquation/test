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
