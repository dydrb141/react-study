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

#### 클래스 컴포넌트

{% tabs %}
{% tab title="클래스형 컴포넌트" %}
```javascript
class Hello extends React.Component {
    render() {
        return <div>안녕하세요. {this.props.name} 님</div>;
    }
};
```
{% endtab %}
{% endtabs %}

### 데이터 주고받기\(props\)

```javascript
const Hello = (props) => {
    return <div>안녕하세요. {props.name}님div>/;<
}

ReactDOM.render(
    <div>
        <Hello name="윤미나" />
        <Hello name="윤인성" />
        <Hello name="윤하늘" />
    </div>,
    document.getElementById('root')
);
```

컴포넌트를 정의하는 함수에 props가 전달 됨.

### 상태와 이벤트 핸들링

#### Index.js

react-scripts를 npm을 통해서 설치하고 react-scripts start를 하게 되면 기본적으로 index 파일을 읽어서 처리하는거 같

{% code title="index.js" %}
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import registerServiceWorker from './registerServiceWorker';

ReactDOM.render(<App />, document.getElementById('root'));
registerServiceWorker();
```
{% endcode %}

#### App컴포넌트

애플리케이션 전체를 나타내는 App 컴포넌트

Todo 애플리케이션을 구성하는 각 컴포넌트를 모아주는 역할

{% code title="App.js" %}
```javascript
import React, { Component } from 'react';
import TodoInput from './TodoInput';
import TodoList from './TodoList';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            tasks: [
                {
                    title: '디폴트 TODO',
                    id: 0,
                },
            ],

            uniqueId: 1,
        }; //state 초기화

        this.addTodo = this.addTodo.bind(this);
        this.resetTodo = this.resetTodo.bind(this);
        //이벤트를 바인드 함. bind는 모든 function 객체가 가지고 있음        
        //bind메서드는 함수 내부에서 사용할 this를 강제(바인드)함
        
    }

    resetTodo() {
        this.setState({
           tasks: [],
        });
    } //setState를 사용해 tasks초기

    addTodo(title) {
        const {
            tasks,
            uniqueId,
        } = this.state;

        tasks.push({
            title,
            id: uniqueId,
        });

        this.setState({
            tasks,
            uniqueId: uniqueId + 1,
        });
    }

    render() {
        /*const tasks = [
            {title: 'Todo 1번째', id: 0},
            {title: 'Todo 2번째', id: 1},
        ];*/

        return (
            <div>
                <h1>TODO App</h1>
                <button onClick={this.resetTodo}>리셋</button>
                <TodoInput addTodo={this.addTodo}/>
                <TodoList tasks={this.state.tasks}/>
            </div>
        );
    }
}

export default App;

```
{% endcode %}

#### TodoInput.js

```javascript
import React, { Component } from 'react';

class TodoInput extends Component{
    constructor(props) {
        super(props);
        this.state = {
            inputValue: '',
        };

        this.handleChange = this.handleChange.bind(this);
        this.handleClick = this.handleClick.bind(this);
    }

    handleChange(e) { //inputBox에 값을 입력받아 state에 setting
                //Hook메소드 임
        this.setState({
            inputValue: e.target.value,
        });
    }

    handleClick(e) {
        e.preventDefault();
        const inputValue = this.state.inputValue;
        this.props.addTodo(inputValue); //외부에서 호출한 property addTodo호출
    }

    render() {
        return (
            <div>
                <input placeholder="새로운 TODO를 입력해주세요" value={this.state.inputValue} onChange={this.handleChange}/>
                <button onClick={this.handleClick}>등록</button>
            </div>
        );
    }
}
export default TodoInput;
```

#### TodoItem

```javascript
import React from 'react';

function TodoItem(props) {
    return (
        <li>
            {props.title}
        </li>
    );
}

export default TodoItem;

```

#### TodoList

Todo목록을 나타냄

```javascript
import React, { Component } from 'react';
import TodoItem from './TodoItem';

class TodoList extends Component{
    render() {
        const list = this.props.tasks.map(todo => {
            return <TodoItem {...todo} key={todo.id} />
        }); //tasks는 배열이기 때문에 map으로 처리
        //map메서드는 배열의 각 요소를 매개변수에 지정한 함수로 처리
        

        return (
            <div>
                <ul>
                    {list}
                </ul>
            </div>
        );
    }
}

export default TodoList;

```

