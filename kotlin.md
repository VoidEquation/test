### 코틀린 개발 삽질기록

## JPA
# JPA Native Query
* JPA Native Query로 count()를 하면 리턴타입이 BigInteger 로 됨
* 해당 데이터를 가공 처리할 때, 코틀린 기본타입으로 변환이 필요함.
* ex) Long 타입으로 변경할 경우 .toLong() 을 사용해야함
* 다른 Map 등 구조에 넣을 경우, nullable이기 때문에 !!.toLong() 을 사용해서 타입변환을 해야함
