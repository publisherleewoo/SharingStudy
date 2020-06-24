## 가비지 컬렉션

자바스크립트는 눈에 보이지 않는 곳에서 메모리 관리를 수행한다.
원시값, 객체, 함수 등 우리가 만드는 모든 것은 메모리를 차지한다.
그렇다면 쓸모 없어지게 되는 것들은 어떻게 처리될까?
지금부터는 자바스크립트 엔진이 어떻게 필요 없는 것을 찾아내 삭제하는지 알아보자.

### 가비지 컬렉션 기준

자바스크립트는 도달 가능성(reachablitity)이라는 개념을 사용해 메모리 관리를 수행한다. `도달 가능한(reachable)` 값은 쉽게 말해 어떻게든 접근하거나 사용할 수 있는 값을 의미한다. 도달 가능한 값은 메모리에서 삭제되지 않는다.

1. 아래에 소개하는 값들은 태생부터 도달 가능하기 때문에, 명백한 이유 없이는 삭제되지 않는다.

- 현재 함수의 지역 변수와 매개 변수
- 중첩 함수의 체인에 있는 함수에서 사용되는 변수와 매개 변수
- 전역 변수
- 기타 등등
  이런 값들은 루트(root)라고 부른다.

2. 루트가 참조하는 값이나 체이닝으로 루트에서 참조할 수 있는 값은 도달 가능한 값이 된다.

자바스크립트 엔진 내에서는 `가비지 컬렉터(garbage collector)`가 끊임없이 동작한다. 가비지 컬렉터는 모든 객체를 모니터링하고, 도달할 수 없는 객체는 삭제한다.

3.