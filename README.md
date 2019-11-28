# 소개

리액트는 페이스북이 개발한 자바 스크립트 라이브러리

### 리액트의 특징

1. Vitural Dom
   1. 리액트가 가상으로 DOM을 관리하는 기능
   2. 다시 랜더링 하는 과정을 리플로우 or 리페인트라 부름
   3. 전체 돔을 변경하지 않고 Vitural Dom에 차이가 있는 부분만 조작해서 변경
   4. 랜더링 성능적 측면에서 좋음
2. JSX

   1. Vitural Dom은 React.createElement라는 메소드로 사용가능 하지만 항상 이걸 사용하긴 힘들다
   2. 다음에 좀더 자세히 설명

### 플럭스란?

사용자 입력을 기반으로 Action을 만들고 Dispatch해서 Store에 저장한 뒤 뷰에 반영하는 흐름으로 애플리케이션을 만드는 아키텍쳐

### 플럭스 구성 요소

![&#xCD9C;&#xCC98;: http://webframeworks.kr/tutorials/react/flux/\(&#xAE40;&#xD0DC;&#xACE4;\)](.gitbook/assets/flux_with_action.png)

#### 뷰\(View\)

리액트 컴포넌트, 사용자가 뷰에 어떤 조작을 하면 조작에 해당하는 액션 생성

#### 액션\(Action\)

* 어떤 행동을 할지 나타내는 객체 ex\) 상품을 구입한다, 상품을 카트에 추가한다. or 대화상자를 출력한다 캐시 데이터 초기화 한다등
* 액션을 디스패치 하면 액션이 스토어로 전달 됨

#### 디스패처\(Dispatcher\)

* 모든 데이터의 흐름을 관리
* 디스패처 데이터는 스토어로 전달 됨

#### 스토어\(Store\)

* 애플리케이션의 상태와 로직을 저장하는 장소
* MVC에서 모델과 비슷한 것
* 애플리케이션 자체 도메인에서 상태를 관리할 수 있다.

### 리덕스란?

* 여러 플럭스의 아키텍처 라이브러리중 하나
* 플럭스의 아키텍처 라이브러리므로 리액트가 아닌 다른 라이브러리\(Angular.js or Vue.js\)와 조합 가능

#### 리덕스 특징

리덕스 3원칙

1. 진실은 하나의 소스로부터
   1. 애플리케이션 모든 상태를 거대한 하나의 객체로 관리
   2. 디버깅과 테스트 쉬움
   3. 모든 곳에서 필요한 상태를 참조할 수 있으므로 구현이 간단해짐
2. 상태는 읽기 전용이다
   1. 컴포넌트에서 애플리케이션 상태를 참조할 수 있지만 변경 불가능
   2. 액션을 디시패치 해야만 애플리케이션 상태 변경 가능
   3. 데이터의 흐름이 한방향으로만 흘러야 복잡해지지 않는다.
3. 변화는 순수 함수로 이뤄져야 한다.
   1. 상태 변경은 부작용 없는 순수 함수 \(순수함수란?  입력값을 넣으면 같은 출력ㅇ 값을 내는 함수\)
   2. 리덕스는 액션을 입력받고 변화한 상태를 출력
   3. 이를 수행하는 순수 함수가 리듀서 

















