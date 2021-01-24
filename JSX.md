리액트는 JSX를 사용해야 한다.

<br>

<h1><b>JSX</b></h1>

자바스크립트를 확장한 문법이다. 자바스크립트의 모든 기능이 포함되어 있다.

<br>

1. JSX에서 태그는 꼭 닫혀야 한다. 아래의 예제에서 input에 close가 되지 않는다면 에러가 발생한다.

```javascript
import React, { Component } from 'react';

class App extends Component {
    render() {
        return(
            <div>
                <input type="text" />
            </div>
        );
    }
}

export default App;
```

<br>

2. 두 개 이상의 엘리먼트는 무조건 하나의 엘리먼트로 감싸 져있어야 한다. Fragment를 이용하면 된다. <div>를 사용해도 되지만 Fragment를 사용하는 것이 더 효율적이다.

```javascript
import React, { Component, Fragment } from 'react';

class App extends Component {
    render() {
        return(
            <Fragment>
                <div> Hello </div>
                <div> Bye </div>
            </Fragment>
        );
    }
}

export default App;
```

<br>

3. 자바스크립트 값을 사용할 수 있다. 출력은 hello alia로 된다.

```javascript
import React, { Component } from 'react';

class App extends Component {
    render() {
        const name = 'alia'
        return(
            <div>
                hello {name}
            </div>
        );
    }
}

export default App;
```

<br>

4. 조건부 렌더링으로 삼항 연산자를 사용할 수 있다. 여기서는 '정답'이 출력된다. false일 땐 '오답'이 출력된다.

```javascript
import React, { Component } from 'react';

class App extends Component {
    render() {
        return(
            <div>
                {
                    10 + 2 === 12
                        ? '정답'
                        : '오답'
                }
            </div>
        );
    }
}

export default App;
```

여기서는 alia로 일치할 경우 '정답' 이 출력되지만, 불일치할 경우 아무것도 나타나지 않는다.

```javascript
import React, { Component } from 'react';

class App extends Component {
    render() {
        const name = 'alia'
        return(
            <div>
                {
                    name === 'alia' && <div>정답</div>
                }
            </div>
        );
    }
}

export default App;
```

<br>

5. camelCase를 사용한다. 일반적인 css는 background-color로 사용한다면 JSX에서는 backgroundColor로 사용한다.

```javascript
import React, { Component } from 'react';

class App extends Component {
    render(){
        const style = {
            backgroundColor: 'black',
            padding: '16px',
            color: 'white',
            fontSize:  '36px'
        };

        return <div style={style}>안녕하세요~!</div>
    }
}

export default App;
```

JSX안에 직접적으로 사용하는 것이 아니라 클래스로 가져오려면 className을 사용해야 한다.

```javascript
import React, { Component } from 'react';
import './App.css';
class App extends Component {
    render(){
        return <div className="App">안녕하세요~!</div>;
    }
}

export default App;
```
```css
/* App.css */
.App{
    background: 'black',
    padding: '16px',
    color: 'white',
    font-size:  '36px'
}
```

<br>

6. 주석을 사용하는 법이 일반적인 //, # , /**/ 과는 조금 다르게 한번 감싸줘야 한다.

```javascript
import React, { Component } from 'react';

class App extends Component {
    render(){
        return (
            <div>
            {/* 주석 처리 */}
                <h1 //주석처리>리액트</h1>
            </div>
        )
}

export default App;
```