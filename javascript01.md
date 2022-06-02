. 공식 문서
ECMAScript의 공식 문서가 궁금하다면 아래 링크를 참고해 보세요.

ECMA-International 공식 ECMA-262문서
>https://www.ecma-international.org/publications-and-standards/standards/ecma-262/

2. 진행 현황
지금까지 제정된 ECMAScript 표준 사항이나 과거 역사가 궁금하다면 아래 링크들을 참고해 보세요.
>https://developer.mozilla.org/ko/docs/Web/JavaScript/Language_Resources

3. 브라우저 지원 현황
각각의 문법별로 브라우저의 지원 여부를 확인하고 싶다면 아래 링크들을 참고해 보세요.
>http://kangax.github.io/compat-table/es6/
한눈에 확인하는 호환성 테이블
문법 검색으로 확인하는 호환성 테이블

4. 버전의 정식 표기
ES6부터는 연호를 사용해서 ES2015, ES2016이라고도 부른다는 점 배웠었죠? 개발자들 사이에서는 짧고 빠르게 소통하기 위해서 ES6, ES7이라는 용어를 사용하지만, 실제로 ECMA International에서 버전을 발표할 때 표기하는 정식 명칭은 연호를 사용해서 ECMAScript 2015라고 표기한다는 점! 참고해 두시면 좋을 것 같습니다.

5. JavaScript vs ECMAScript
간혹 JavaScript와 ECMAScript가 똑같다고 오해하는 경우가 있는데요. 둘 사이에는 명확한 차이가 있습니다!

일단 첫 번째 차이점은, JavaScript는 프로그래밍 언어이고, ECMAScript는 프로그래밍 언어의 표준입니다. 
쉽게 생각하면 ECMAScript는 JavaScript가 갖추어야 할 내용을 정리해둔 '설명서'이고, JavaScript는 ECMAScript를 준수해서 만들어낸 '결과물' 이라고 생각할 수 있는데요. 참고로 ECMAScript가 JavaScript화 하기 위해 등장하긴 했지만, ECMAScript는 JavaScript 뿐만아니라 모든 스크립트 언어(scripting languages)가 지켜야 하는 표준입니다. 만약 여러분이 자바스크립트와 같은 언어를 직접 만들고자 한다면, 이 ECMAScript를 준수해야 한다는 것이죠!

그리도 두 번째 차이점은 JavaScript는 ECMAScript를 기반으로 하지만 ECMAScript에 정의된 내용뿐만 아니라, 다른 부가적인 기능도 있다는 겁니다. 
특히, 우리가 자바스크립트로 HTML 코드를 제어하기 위해 사용하는 DOM(Document Object Model)을 다루는 문법들은 ECMAScript에 표준화된 문법이 아니라 WebIDL에서 표준화된 기술이라고 할 수 있습니다.
