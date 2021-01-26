<b>Props</b>와 <b>State</b>는 리액트에서 정말 중요한 개념이다. 

리액트에서 데이터를 다룰 때 사용된다.

- <b>Props</b>는 부모 컴포넌트가 자식 컴포넌트한테 값을 전달할 때 사용된다. 값을 직접 바꿀 수는 없고 부모 컴포넌트로부터 받아오기만 할 수 있다.
- <b>State</b>는 컴포넌트 내부에서 선언하며 setState로 내부에서 값을 변경할 수 있다.

<br>

<h1><b>Props</b></h1>

```javascript
import React, { Component } from 'react';

class ChildClass extends Component {
    render(){
        return(
            <div> 이 컴포넌트는 <b>{this.props.name} 컴포넌트 입니다.</b></div>
        );
    }
}

export default ChildClass;
```
```javascript
import React, { Component } from 'react';
import ChildClass from './ChildClass';

class App extends Component{
    render(){
        return(
            <ChildClass name="자식" />
        );
    }
}

export default App;
```
<br>

이렇게 되면 화면에는 '이 컴포넌트는 자식 컴포넌트입니다.'라는 문장이 출력된다. 즉, import로 컴포넌트를 불러오고 렌더링 하는 것이다.

혹시나 props를 빠뜨리거나 일부러 비워둬야 할 때라면, <b>defaultProps</b>를 사용해 props의 기본값을 설정해줄 수 있다. 두 가지 방법이 있다.

이는 App 컴포넌트에서 name을 지정하지 않았을 때 사용한다.

```javascript
import React, { Component } from 'react';

class ChildClass extends Component{
    static defaultProps = {
        name : '기본이름을 가진'
    }
    render(){
        return(
            <div> 이 컴포넌트는 <b>{this.props.name} 컴포넌트 입니다.</b></div>
        );
    }
}

export default ChildClass;
```
```javascript
import React, { Component } from 'react';

class ChildClass extends Component{
    render(){
        return(
            <div> 이 컴포넌트는 <b>{this.props.name} 컴포넌트 입니다.</b></div>
        );
    }
}

ChildClass.defaultProps = {
    name: '기본이름을 가진'
};

export default ChildClass;
```

<br>

<h1><b>함수형 컴포넌트</b></h1>
props만 사용할 때는 <b>함수형 컴포넌트</b>로 더 간단하게 표현할 수 있다. 함수형 컴포넌트와 클래스형 컴포넌트의 차이는 함수형 컴포넌트에는 state와 LifeCycle이 빠진 것이다. 따라서 메모리 자원을 덜 사용하기에 많은 컴포넌트를 렌더링 할 때 성능 차이가 나게 된다.

```javascript
import React from 'react';

const ChildClass = ({name}) => {
    return(
        <div>
        이 컴포넌트는 <b>{this.props.name} 컴포넌트 입니다.</b>
        </div>
    );
};

export default ChildClass;
```

<br>

<h1><b>State</b></h1>

props는 값을 바꾸지 못한다면 <b>state</b>는 동적인 데이터를 다룬다. 컴포넌트의 state를 정의할 때는 <b>class fields</b> 문법을 사용해서 정의한다. 이유는 편의를 위해서다. constructor에 넣으면 super(props)를 호출해야 한다. 만약 constructor와 class fields를 같이 사용하게 되면 class fields가 먼저 실행된다. 

```javascript
import React, { Component } from 'react';

class Counter extends Component {
    state = {
        number: 0
    }

    handleIncrease = () => {
        this.setState({
            number: this.state.number + 1
        });
    }

    handleDecrease = () => {
        this.setState({
            number: this.state.number - 1
        });
    }

    render(){
        return(
            <div>
                <h1>Counter</h1>
                <div>값 : {this.state.number} </div>
                <button onClick = {this.handleIncrease}>+</button>
                <button onClick = {this.handleDecrease}>-</button>
            </div>
        );
    }
}

export default Counter;
```

<b>setState</b>는 객체로 전달되는 값만 업데이트 해주며 호출되면 컴포넌트가 리렌더링 된다. 하지만 setState는 객체의 깊숙한 곳까지 확인하지 못한다. 이때는 자바스크립트의 전개 연산자인... 을 사용해주어야 한다. 기존의 객체 안의 내용을 해당 위치에다가 풀어주는 것이다.

또한 setState를 객체 대신 함수를 전달하고 싶다면 아래와 같이 하면 된다.

```javascript
const { number } = this.state;
this.setState({
    number: number + 1
})
```
button 부분에서 html과 다른점은 <b>리액트는 camelCase를 사용</b>해줘야한다. 예를 들어, html은 onclick, react는 onClick이다. 또한 이벤트를 에 전달해주는 값은 함수여야만 한다. 그렇지 않고 메서드를 호출하게 된다면 매번 함수가 호출이 되어 무한 반복이 되어버린다.

<br>

참고 : <a>https://velopert.com/3629</a>
