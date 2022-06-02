# Symbol
심볼(symbol)은 기본형 데이터 타입(primitive data type) 중 하나입니다. 심볼은 코드 내에서 유일한 값을 가진 변수 이름을 만들 때 사용하는데요.

const user = Symbol();
일단, 이렇게 Symbol이라는 함수를 통해서 심볼 값을 만들어 낼 수 있습니다.

const user = Symbol('this is a user');
그리고 괄호 안에 심볼에 대한 설명을 붙일 수도 있습니다. 이렇게 Symbol 값을 담게 된 user라는 이름의 변수는 다른 어떤 값과 비교해도 true가 될 수 없는 고유한 변수가 되는데요.

const user = Symbol('this is a user');
```
user === 'this is user'; // false
user === 'user'; // false
user === 'Symbol'; // false
user === true; // false
user === false; // false
user === 123; // false
user === 0; // false
user === null; // false
user === undefined; // false
```
심지어는 똑같은 설명을 붙인 심볼을 만들더라도 두 값을 비교하면 false가 반환된다.
```
const symbolA = Symbol('this is Symbol');
const symbolB = Symbol('this is Symbol');

console.log(symbolA === symbolB); // false
```

## BigInt
BigInt는 자바스크립트에서 아주 큰 정수(Integer)를 표현하기 위해 등장한 데이터 타입이다.
사실 자바스크립트의 숫자에는 안전한 정수 표현의 한계가 있는데요. 안전한 정수 표현하기 위해서 자바스크립트에서 안전한 최대 정수는 2**53 - 1, 안전한 최소 정수는 -(2**53 - 1) 입니다. 
2**53 - 1은 구체적으로 9007199254740991이라는 숫자로 약 9,000조 정도의 숫자인데요. 안전한 정수 표현이라는 의미는 자바스크립트에서 이 숫자 범위를 초과하는 정숫값을 사용하려고 하면 연산에 미세한 오류가 발생한다는 뜻입니다.

9007199254740991 + 1과 9007199254740991 + 2를 비교하면 true라는 결과가 리턴되다. 실제로 콘솔에 9007199254740991 + 2과 심지어 9007199254740993을 출력해봐도 9007199254740993이 아니라 9007199254740992가 출력되는 모습을 확인할 수 있는데요.
```
console.log(9007199254740991 + 1 === 9007199254740991 + 2); // true
console.log(9007199254740991 + 2); /// 9007199254740992
console.log(9007199254740993); /// 9007199254740992
```
이 숫자 범위는 JavaScript가 IEEE 754에 기술된 배정밀도 부동소수점 형식 숫자체계를 사용하기 때문이다.혹시 용어가 너무 어색하다거나 개념이 조금 어렵다면, 일단은 자바스크립트의 숫자형(number type) 값에는 9000조 정도의 정수 표현의 한계가 존재한다. 정도만 이해해 주세요!
사실 9,000조라는 숫자도 꽤 큰 숫자기 때문에 대부분 상황에서는 큰 문제가 되지 않는데요. 그래도 암호 관련 작업이나 계산기 관련 작업을 할 때, 아주 큰 숫자를 다루거나 혹은 굉장히 정확한 연산이 필요한 상황에서 이보다 더 큰 숫자가 필요할 수도 있겠죠?

그럴 때 바로 BigInt라는 데이터 타입의 값을 사용하면 됩니다. BigInt 타입의 값은 일반 정수 마지막에 알파벳 n을 붙이거나 BinInt라는 함수를 사용하면 되는데요.


```
console.log(9007199254740993n); // 9007199254740993n
console.log(BigInt(9007199254740993)); // 9007199254740993
```

이렇게 BigInt 타입을 사용하면 2**53 - 1 보다 큰 정숫값도 안전하게 표현할 수가 있습니다. 단, BigInt 타입에는 몇 가지 주의사항이 있는데요. 일단 BigInt 타입은 말 그대로 큰 정수를 표현하기 위한 데이터 타입이기 때문에 소수 표현에는 사용할 수가 없습니다.

1.5n; // SyntaxError
그래서 소수 형태의 결과가 리턴되는 연산은 소수점 아랫부분은 버려지고 정수 형태로 리턴됩니다.

10n / 6n; // 1n
5n / 2n; // 2n
그리고 BigInt 타입끼리만 연산할 수 있고, 서로 다른 타입끼리의 연산은 명시적으로 타입 변환을 해야 합니다.

3n * 2; // TypeError
3n * 2n; // 6n
Number(3n) * 2; // 6
큰 범위의 정수를 안전하게 사용할 수 있다는 장점이 있지만, 이런 제한사항들 때문에 실제로 BigInt 타입의 값을 활용할 상황들이 그리 흔하지는 않다.

# typeof 연산자
지금까지 계속해서 자바스크립트의 데이터 타입에 대해서 살펴보고 있는데요. 우리가 사용하는 값이 어떤 데이터 타입을 가지고 있는지 확인하려면 typeof 연산자를 사용해야 합니다.
typeof 연산자는 키워드 다음에 공백(띄어쓰기)을 두고 값을 작성해도 되고, 함수를 사용하듯 괄호로 감싸서 사용할 수 있다.
```
typeof 'Codeit'; // string
typeof Symbol(); // symbol
typeof {}; // object
typeof []; // object
typeof true; // boolean
typeof(false); // boolean
typeof(123); // number
typeof(NaN); // number
typeof(456n); // bigint
typeof(undefined); // undefined
```
하지만 한 가지 주의해야 할 점은 typeof 연산자의 결과가 모든 타입과 1:1로 매칭되지 않는다는 점이다.

1. null이 object라고?
  일단, typeof null을 하면 문자열 null이 리턴되는 게 아니라 문자열 object가 리턴된다.

2. typeof null; // object
  이건 자바스크립트가 처음 구현될 때의 특별한 문법 설계 때문입니다. 나중에 ECMAScript에서 수정이 제안되었었지만, 이미 개발된 많은 프로젝트에 버그가 생기는 우려로 인해 반영되지 않고 있습니다.

3. function?
  그리고 함수에 typeof 연산자를 사용하면 function이라는 값을 리턴하는데요.
```
function sayHi() {
  console.log('Hi!?');
}
```
4. typeof sayHi; // function
자바스크립트에서 함수는 객체로 취급된다. typeof 연산자를 함수에 사용하면 function이 리턴된다.