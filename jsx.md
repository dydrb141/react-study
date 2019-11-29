# JSX

JSX는 HTML을 사용해 리액트를 개발 할 수 있다.

트랜스 파일러를 통해 React.createElement형태로 변환해서 사용한다.

### JSX 문법

#### 스코프에 React가 있어야함.

JSX태그는 React.createElement 함수를 호출하는 형태로 변환 하기때문에 React를 임포트 해줘야함.

```text
import React from 'react';
```

#### 인라인 표현식

{% tabs %}
{% tab title="인라인 표현식" %}
```javascript
const fullNames = {
    inseong: '윤인성',
    mina: '윤미나',
    sky: '윤하늘',
};

const getFullName = nickname => fullNames[nickname];
const element = <h1> Hello, {getFullName('inseong')}</h1>;
```
{% endtab %}
{% endtabs %}

#### 속성지정

* HTML태그와 거의 같음
* 표현식 {} 로도 가능
* HTML처럼 속성 이름만 지정 가능 
* 자바스크립트 예약어는 사용할 수 없으므로 JSX는 class 속성을 className으로, for 속성을 htmlFor로 사

{% tabs %}
{% tab title="속성 지정" %}
```javascript
const element = <input type="text" value="some valu" />;
```
{% endtab %}

{% tab title="표현식 지정" %}
```javascript
const inputValue = 'some value';
const element = <input type="text" value={inputValue} />;
```
{% endtab %}

{% tab title="속성 이름만 지정" %}
```javascript
const element1 = <input type="checkbox" checked />;
const element2 = <input type="checkbox" checked={true} />; //위와 동일
```
{% endtab %}
{% endtabs %}

#### 자식 요소에 배열 전달

```javascript
const list = (
    <ul>
        {[1, 2, 3].map(num => <li>{num}</li>)}
    </ul>
)        
```

### 바벨을 사용해 JSX를 자바스크립트로 변환하기

#### 트랜스파일러와 바벨

JSX는 트랜스파일러를 기반으로 자바스크립트로 변환해야 실행 가능\(대표적 커피스크립트 ,타입스크립트, 바벨\)

### CLI

npm으로 필요 패키지 설치

```javascript
$ midir babel-cli-example
$ cd babel-cli-example
$ echo "{}" > package.json
$ npm install --save-dev babel-cli babel-preset-react
```



#### 웹팩이란?

* 모듈 번들러라고 부르는 도구
* CommonJS모듈 형식으로 작성된 소스 파일을 묶어서  정적 자바스크립트 파일로 출력







