# AND 와 OR 연산자의 연산 우선순위

```
function checkAnswer(value) {
  if (value < 10 && value > 0 && value !== 3) {
    return '정답입니다!';
  } 

  return '틀렸습니다!';
}

console.log(checkAnswer(4)); // 정답입니다!
```

파라미터 value로 전달되는 값이 10보다 작으면서 0보다는 크고, 그러면서도 3은 아닐 때 '정답입니다!' 라는 문자열을 콘솔에 출력하는 함수를 정의했는데요. 코드를 작성하다 보면 다양한 상황을 고려하기 위해서 이렇게 AND나 OR 연산자를 여러 번 사용해야 할 수도 있습니다.

그런데 한 가지 조심해야 할 부분이 있는데요. 위에 있는 코드처럼 AND 연산자나 OR 연산자 중 하나만 계속해서 사용할 때는 문제 없지만, 만약 AND 연산자와 OR 연산자를 섞어서 사용할 때는 연산의 우선순위가 존재한다는 겁니다. 쉽게 설명해서 1 + 2 + 3 처럼 계속해서 더하기 연산자만 사용한다면 왼쪽부터 차례대로 더하면 되지만, 1 + 2 * 3 처럼 더하기와 곱하기 연산자가 섞여 있다면 연산자 우선순위를 고려해야 한다는 것이죠.
곱하기 연산자가 더하기 연산자보다 연산 우선순위가 높다는 사실 모두 알고 계시죠? AND 와 OR 연산자 사이에서는 AND 연산자의 우선순위가 더 높습니다.
```
console.log(true || false && false); // true
console.log((true || false) && false); // false

console.log('Codeit' || NaN && false); // Codeit
console.log(('Codeit' || NaN) && false); // false
```
위 코드처럼 OR 연산자 뒤에 AND 연산자를 사용한다면, 소괄호로 OR 연산을 감쌀 때와 감싸지 않았을 때 서로 다른 결과를 보여주는 걸 확인할 수 있는데요. 프로그래밍을 하다 보면 AND와 OR 연산자뿐만 아니라 다양한 연산자들을 복합적으로 사용하게 될 텐데, 연산의 우선순위를 명확하게 하지 않으면 예상치 못한 결과를 얻을 수 있으니 잘 구분해두는 것이 중요합니다.
대부분은 코드를 작성하고 테스트도 해보면서 자연스럽게 이해되기 때문에 하나하나 시험공부 하듯 외울 필요는 없지만 간혹 우리가 의도하지 않은 연산 결과가 나타날 땐, 이 연산자 우선순위를 의심해 보시고 아래 링크의 도움을 받는 것도 좋을 것 같습니다.

연산자 우선순위

하지만 여러분이 코드를 작성할 때, 특히 여러 사람과 함께 협업하는 상황에서 다양한 연산자들을 복합적으로 사용해야 한다면 소괄호를 활용해서 의도에 맞는 연산 우선순위를 명확하게 표기하는 것이 좋은 습관이라는 점도 잘 기억해 두시면 좋을 것 같습니다.
```
console.log(true || (false && false)); // true
console.log((true || false) && false); // false

console.log('Codeit' || (NaN && false)); // Codeit
console.log(('Codeit' || NaN) && false); // false
```