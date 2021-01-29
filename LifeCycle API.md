<b>LifeCycle</b>은 리액트에서 컴포넌트를 만들어낼 때 중요하다.

컴포넌트가 브라우저에서 <b>나타날 때(Mounting), 업데이트될 때(Updating : 컴포넌트의 props나 state가 바뀔 때), 사라질 때(Unmounting)</b> 등에 사용된다.

|Mounting	|Updating	|Unmounting|
|-----|-----|-----|
|constructor, getDerivedStateFromProps, componentDidMount|	getDerivedStateFromProps, shouldComponentUpdate, getSnapshotBeforeUpdate, componentDidUpdate|	componentWillUnmount |

<br>

<b><h1>constructor</h1></b>
생성자 함수이다. 우리가 만든 컴포넌트가 처음 브라우저에 나타날 때 만들어지는 과정에서 가장 먼저 실행되는 함수이다. 컴포넌트가 가지고 있는 state를 초기 설정하거나 미리 해야 하는 작업이 있다면 사용한다.

<br>

<b><h1>getDerivedStateFromProps</h1></b>
props로 받은 값을 state에다가 동기화시키고 싶을 때 사용한다. mounting, updating 둘 다 사용한다.

<br>

<b><h1>shouldComponentUpdate</h1></b>
정말 중요한 함수다. 컴포넌트가 업데이트 되는 성능을 최적화시키고 싶을 때 사용한다. 부모 컴포넌트가 리렌더링 되면 자식 컴포넌트도 렌더링이 실행된다. virtual DOM에 그리는 성능도 최적화시키고 싶을 때 사용한다. true / false를 반환하는데 true를 반환하면 렌더링 프로세스를 진행하고 false를 반환하면 중지된다. 즉 virtual DOM에도 렌더링 할지 말 지 결정한다. 

<br>

<b><h1>getSnapshotBeforeUpdate</h1></b>
렌더링 한 결과를 브라우저 상에 반영되기 바로 직전에 호출되는 함수라고 생각하면 된다. 업데이트 바로 하기 직전 스크롤의 위치나 해당 DOM의 크기를 가져오고 싶을 때 사용한다.

<br>

<b><h1>componentDidMount</h1></b>
실제로 브라우저 상에 나타나는 시점에, 차트나 네트워크 요청, api 요청을 처리한다.

<br>

<b><h1>componentDidUpdate</h1></b>
이전의 상태와 현재의 상태가 페이지가 바꼈을 때 어떤 작업을 할 때 사용된다.

<br>

<b><h1>componentWillUnmount</h1></b>
컴포넌트가 사라지는 과정에서 호출되는 함수이다.

<br>

<b><h1>componenetDidCatch</h1></b>
에러가 발생한 걸 보여줄수도, 특정 서버에게 넘겨줄 수도 있다. 부모 컴포넌트에서 작성해야 한다.