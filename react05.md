

# 디자인을 적용하는 방법
## 이미지 불러오기
이미지 파일은 import 구문을 통해 불러오고, 불러온 이미지 주소를 src 속성으로 사용하면 됩니다.
```
import diceImg from './assets/dice.png';

function Dice() {
  return <img src={diceImg} alt="주사위 이미지" />;
}

export default App;
```

### 인라인 스타일
리액트에서 인라인 스타일은 문자열이 아닌 객체형으로 사용합니다. 프로퍼티 이름은 CSS 속성 이름으로, 프로퍼티 값은 CSS 속성 값으로 쓰는데요, 이때 프로퍼티 이름은 아래의 boarderRadius 처럼 대시 기호 없이 카멜 케이스로 써야 한다는 점도 꼭 기억해두세요.
```
import diceImg from './assets/dice.png';

const style = {
  borderRadius: '50%',
  width: '120px',
  height: '120px',
};

function Dice() {
  return <img style={style} src={diceImg} alt="주사위 이미지" />;
}

export default App;
```
## CSS 파일 불러오기
import 구문으로 파일을 불러올 수 있는데요, 이때 from 키워드 없이 쓰면 됩니다.
```
import diceImg from './assets/dice.png';
import './Dice.css';

function Dice() {
  return <img src={diceImg} alt="주사위 이미지" />;
}

export default App;
```

## 클래스네임 사용하기
CSS 파일에 정의된 클래스명을 className prop에 문자열로 넣어주면 됩니다. 이때 재사용성을 위해 className prop을 부모 컴포넌트에서 받으면 더 좋습니다.
```
import diceImg from './assets/dice.png';
import './Dice.css';

function Dice({ className = '' }) {
  const classNames = `Dice ${className}`;
  return <img className={classNames} src={diceImg} alt="주사위 이미지" />;
}

export default App;
```

### 편리하게 클래스네임을 쓰는 방법
앞에서는 여러 className을 템플릿 문자열로 합쳐서 사용했습니다. 몇 개 없을 때는 상관없지만, 개수가 늘어날수록 아래처럼 알아보기 힘들어진다는 문제점이 있는데요.

> 템플릿 문자열을 사용한 예
```
function Button({ isPending, color, size, invert, children }) {
  const classNames = `Button ${isPending ? 'pending' : ''} ${color} ${size} ${invert ? 'invert' : ''}`;
  return <button className={classNames}>{children}</button>;
}

export default Button;
```
> 배열을 사용한 예
```
function Button({ isPending, color, size, invert, children }) {
  const classNames = [
    'Button',
    isPending ? 'pending' : '',
    color,
    size,
    invert ? 'invert' : '',
  ].join('');
  return <button className={classNames}>{children}</button>;
}

export default Button;
```
위 예시 코드처럼 지저분하게 느껴지고, 매번 반복되는 코드를 작성한다는 번거로움이 있습니다. 개발자들은 이럴 때 라이브러리라는 걸 쓰는데요, 다른 개발자가 미리 만들어 놓은 코드를 이용해서 편하게 개발하는 겁니다.

클래스네임의 경우에도 편리하게 사용할 수 있는 라이브러리가 많이 있는데요, 그중에서도 이번에 소개할 라이브러리는 바로 classnames라는 라이브러리입니다. 아래 예시 코드를 보시면 아시겠지만, 클래스네임에만 집중할 수 있어 훨씬 읽기 편해집니다. 이렇게 적절한 라이브러리를 쓰면 개발 생산성이 굉장히 좋아지죠.

> classnames 라이브러리를 사용한 예
```
import classNames from 'classnames';

function Button({ isPending, color, size, invert, children }) {
  return (
    <button
      className={classNames(
        'Button',
        isPending && 'pending',
        color,
        size,
        invert && 'invert',
      )}>
     { children }
   </button >
  );
}

export default Button;
```
classnames 은 NPM이라는 프로그램을 통해 설치할 수 있습니다. 터미널에서 npm install classnames 을 입력하고 설치한 다음에, 위 예시처럼 import 로 불러와서 사용하면 됩니다. NPM 저장소 사이트로 들어가면 사용 방법과 설명이 나와있으니, 아래 링크를 한 번 살펴보시고 사용해보는 것도 좋을 것 같습니다.

NPM classnames 패키지: https://www.npmjs.com/package/classnames