null 병합 연산자 ??
물음표 두 개(??)를 사용해서 null 혹은 undefined 값을 가려내는 연산자 입니다.
아래 코드를 보세요.

const example1 = null ?? 'I';
const example2 = undefined ?? 'love';
const example3 = 'Codeit' ?? 'JavaScript';

console.log(example1, example2, example3); // ?
example1과 2를 보시면, 지금 null 병합 연산자 왼편에 각각 null과 undefined가 있죠? 이렇게 연산자 왼편의 값이 null 이나 undefined라면 연산자 오른편의 값이 리턴되고, example3처럼 연산자 왼편의 값이 null 이나 undefined가 아니라면 연산자 왼편의 값이 리턴되는 원리로 동작합니다. 결과적으로 마지막 줄에서 콘솔에 출력되는 값은 I love Codeit이 되겠죠?

const example1 = null ?? 'I'; // I
const example2 = undefined ?? 'love'; // love
const example3 = 'Codeit' ?? 'JavaScript'; // Codeit

console.log(example1, example2, example3); // I love Codeit
OR 연산자(||)와 비교
그런데 이렇게 보니깐 이전에 앞서 OR 연산자 (||)와 동작하는 방식이 비슷해 보입니다. 실제로도 다음과 같은 상황이라면 똑같이 동작을 하게 되는데요.

const title1 = null || 'codeit';
const title2 = null ?? 'codeit';

console.log(title1); // codeit
console.log(title2); // codeit
하지만 null 병합 연산자(??)는 왼편의 값이 null이나 undefined인지 확인하고 OR 연산자(||)는 왼편의 값이 falsy인지를 확인하기 때문에 아래 코드와 같이 null이나 undefined가 아닌 falsy 값을 활용할 때 결과가 서로 다르니깐, 이 부분은 꼭 기억해 두세요!

const title1 = false || 'codeit';
const title2 = false ?? 'codeit';

console.log(title1); // codeit
console.log(title2); // false

const width1 = 0 || 150;
const width2 = 0 ?? 150;

console.log(width1); // 150
console.log(width2); // 0