# JSX란?
JSX는 자바스크립트의 확장 문법인데요. 리액트로 코드를 작성할 때 HTML 문법과 비슷한 이 JSX 문법을 활용하면 훨씬 더 편리하게 화면에 나타낼 코드를 작성할 수가 있게 됩니다.

`import ReactDOM from 'react-dom';`

`ReactDOM.render(<h1>안녕 리액트!</h1>, document.getElementById('root'));`

## JSX 문법
JSX는 자바스크립트로 HTML을 작업할 수 있도록 한다.

HTML과 다른 속성명
1. 속성명은 카멜 케이스로 작성하기!
JSX 문법에서도 태그에 속성을 지정해 줄 수 있습니다. 단, 여러 단어가 조합된 몇몇 속성들을 사용할 때는 반드시 카멜 케이스(Camel Case)로 작성해야 합니다.

 onclick, onblur, onfocus -> onClick, onBlur, onFocus, onMouseDown, onMouseOver, tabIndex 
```
import ReactDOM from 'react-dom';

ReactDOM.render(
  <button onClick= ... >클릭!</button>,
  document.getElementById('root')
);
```
단, 예외적으로 HTML에서 비표준 속성을 다룰 때 활용하는 data-* 속성은 카멜 케이스(Camel Case)가 아니라 기존의 HTML 문법 그대로 작성하셔야 합니다.

```
import ReactDOM from 'react-dom';

ReactDOM.render(
  <div>
    상태 변경: 
    <button className="btn" data-status="대기중">대기중</button>
    <button className="btn" data-status="진행중">진행중</button>
    <button className="btn" data-status="완료">완료</button>
  </div>,
  document.getElementById('root')
);
```

2. 자바스크립트 예약어와 같은 속성명은 사용할 수 없다

  for ->htmlFor
  class -> className
   ```
    import ReactDOM from 'react-dom';

    ReactDOM.render(
      <form>
        <label htmlFor="name">이름</label>
        <input id="name" className="name-input" type="text" />
      </form>,
      document.getElementById('root')
    );
    ```
3. JSX 문법을 활용할 때는 반드시 하나의 요소로 감싸주어야 합니다.

  1. 방법1
    ```
    import ReactDOM from 'react-dom';
    ReactDOM.render(
      <div>
        <p>안녕</p>
        <p>리액트!</p>
      </div>,
      document.getElementById('root')
    ```

  2. Fragment 사용하기
    ```
    import { Fragment } from 'react';
    import ReactDOM from 'react-dom';
    ReactDOM.render(
    <Fragment>
      <p>안녕</p>
      <p>리액트!</p>
    </Fragment>,
    document.getElementById('root')
          );
    ```
  3. <></> 사용하기
    ```
    import ReactDOM from 'react-dom';
    ReactDOM.render(
      <>
        <p>안녕</p>
        <p>리액트!</p>
      </>,
    document.getElementById('root')
    );
    ```
4. 자바스크립트 표현식 넣기 
JSX 문법에서 중괄호({})를 활용하면 자바스크립트 표현식을 넣을 수 있습니다.
  ```
  import ReactDOM from 'react-dom';

  const product = '맥북';

  ReactDOM.render(
    <h1>나만의 {product} 주문하기</h1>,
    document.getElementById('root')
  );
  ```
이런 부분들을 잘 활용하면, 아래 코드처럼 중괄호 안에서 문자열을 조합할 수도 있고 변수에 이미지 주소를 할당해서 img 태그의 src 속성값을 전달해 줄 수도 있고, 이벤트 핸들러를 좀 더 편리하게 등록할 수도 있습니다.

import ReactDOM from 'react-dom';

const product = 'MacBook';
const model = 'Air';
const imageUrl = 'https://upload.wikimedia.org/wikipedia/commons/thumb/1/1e/MacBook_with_Retina_Display.png/500px-MacBook_with_Retina_Display.png'

function handleClick(e) {
  alert('곧 도착합니다!');
}

ReactDOM.render(
  <>
    <h1>{product + ' ' + model} 주문하기</h1>
    <img src={imageUrl} alt="제품 사진" />
    <button onClick={handleClick}>확인</button>
  </>,
  document.getElementById('root')
);

단, JSX 문법에서 중괄호는 자바스크립트 표현식을 다룰 때 활용하기 때문에, 중괄호 안에서 for, if문 등의 문장은 다룰 수 없다 또한 JSX 문법을 활용할 때 조건문이 꼭 필요하다면 조건 연산자를, 반복문이 꼭 필요하다면 배열의 반복 메소드를  활용한다.
