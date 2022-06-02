# 리액트 엘리먼트
JSX 문법으로 작성한 요소는 결과적으로 자바스크립트 객체가 됩니다.
```
import ReactDOM from 'react-dom';

const element = <h1>안녕 리액트!</h1>;
console.log(element);
ReactDOM.render(element, document.getElementById('root'));
```
`{$$typeof: Symbol(react.element), type: "h1", key: null, ref: null, props: {…}, …}`

이런 객체를 리액트 엘리먼트라고 부르는데요.


이 리액트 엘리먼트를 ReactDOM.render 함수의 아규먼트로 전달하게 되면, 리액트가 객체 형태의 값을 해석해서 HTML 형태로 브라우저에 띄워주는 것이죠.

리액트 엘리먼트는 리액트로 화면을 그려내는데 가장 기본적인 요소입니다.

## 리액트 컴포넌트
리액트 컴포넌트는 리액트 엘리먼트 간편하게 만들 수 있는 문법이다.

1. 생성자 객체 방법
```
import ReactDOM from 'react-dom';

function Hello() {
  return <h1>안녕 리액트</h1>;
}

const elem`ent = (
  <>
    <Hello />
    <Hello />
    <Hello />
  </>
);

ReactDOM.render(element, document.getElementById('root'));
```

그리고 이렇게 컴포넌트를 작성하면,
위 코드에서 element 변수 안의 JSX 코드에서 볼 수 있듯 컴포넌트 함수 이름을 통해 하나의 태그처럼 활용할 수가 있습니다.

이런 특성을 모듈 문법으로 활용하면 훨씬 더 독립적으로 컴포넌트 특성에 집중해서 코드를 작성할 수가 있습니다.

예시: Dice.js

import diceBlue01 from './assets/dice-blue-1.svg';

function Dice() {
  return <img src={diceBlue01} alt="주사위" />;
}

export default Dice;
예시: App.js

import Dice from './Dice';

function App() {
  return (
    <div>
      <Dice />
    </div>
  );
}

export default App;


한 가지 주의해야 할 부분은, 리액트 컴포넌트의 이름은 반드시 첫 글자를 대문자로 작성해야 한다는 것입니다.
컴포넌트 이름의 첫 글자가 소문자라면 오류가 발생하니깐 꼭 주의해 주세요!