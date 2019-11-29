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
{% endtabs %}



