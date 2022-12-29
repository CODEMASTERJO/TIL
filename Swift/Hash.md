# TIL(22.12.29)

## **Hash**

"jojo" -> (해쉬함수) -> 12345(hash value)
"jenna" -> (해쉬함수) -> 12445
"jason" -> (해쉬함수) -> 12733

hashTable
jojo / 12345
jenna / 12445
jason / 12733

hash값 = 유일한 값(유일성 보장)
딕셔너리(set)가 값을 빨리 찾는 이유는? hash값을 통해 key값을 찾아낸다.
-> key값은 Hashable하다 

어떤 타입이 Hashable하다 = 해쉬함수에서 input으로 사용할 수 있다.

커스텀 타입은 Hashable 하지 않다.
-> (해결) Hashable 프로토콜 채택


Equatable(==, !=)
- Comparable(<, >, <=, >=)
- Hashable(hash(into:))

set에 원소가 될 수 있다 -> 해셔블하다.

Hashable 채택
1. 열거형
  - 연관값이 없다면 값의 유일성이 보장되어 Hashable 채택하지 않아도 됨

2. 구조체
  - hash into
  ```swift
  func hash(into hasher: inout Hasher) {
    hasher.combine(저장속성)
    hasher.combine(저장속성)
  }
  ```
3. 클래스
  - Hashalbe 프로토콜 채택 시, Equatable도 구현해줘야한다

프로토콜
Equata