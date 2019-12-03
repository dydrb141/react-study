# 리액트 컴포넌트

### 함수형 컴포넌트와 클래스형 컴포넌트

리액트 컴포넌트는 크게 함수형 컴포넌트와 클래스형 컴포넌트로 나뉜다.

#### 함수형 컴포넌트

{% tabs %}
{% tab title="JavaScript" %}
```javascript
import React from 'react'

const Hello = (props) => {
 return <div>안녕하세요. {props.name}님</div>;
 };
```
{% endtab %}
{% endtabs %}



