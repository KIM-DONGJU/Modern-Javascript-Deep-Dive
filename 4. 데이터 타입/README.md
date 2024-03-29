# 데이터 타입
자바스크립트의 타입은 크게 원시 타입과 객체 타입으로 나눌 수 있다. 원시 타입은 숫자 타입, 문자열 타입, 불리언 타입, undefined 타입, null 타입, 심벌 타입이 있고, 객체 타입은 객체, 함수, 배열 등이 있다.


### 4.1 숫자 타입
다른 언어의 경우 int, long, float 등 다양한 숫자 타입이 있기도 한데, 자바스크립트는 하나의 숫자 타입만 존재한다.
자바스크립트의 숫자 타입의 값은 배정밀도 64비트 부동소수점 형식을 따르는데, 이는 모든 수를 실수로 처리하는 것을 의미한다.
```
console.log(10 / 0); // Infinity
console.log(10 / -0); // -Infinity
```
위와 같이 독득한 값도 존재한다.


### 4.2 문자열 타입
문자열은 0개 이상의 16비트 유니코드 문자의 집합으로 전 세계 대부분의 문자를 표현할 수 있다.
문자열은 작은따옴표(''), 큰따옴표(""), 백틱(``)으로 텍스트를 감싸는 방식으로 표현하는데, 따옴표로 감싸는 이유는 키워드나 식별자 같은 토큰과 구분하기 위해서이다. 따옴표로 감싸지 않으면 자바스크립트 엔진은 키워드나 식별자 같은 토큰으로 인식한다.
자바 스크립트에서의 문자열은 원시타입이며, 변경 불가능한 값이다. 이것은 문자열이 생성되면 그 문자열을 변경할 수 없다는 것을 의미한다.
```
var string = '문자열1';
string = '문자열2';
```
위와 같이 코드를 보면 먼저 '문자열1'이 메모리 주소에 저장되고 string 이라는 식별자가 그 메모리 주소를 가리킨다. 그 후 '문자열2'가 메모리 주소에 저장되고 string이 '문자열2'에 대한 메모리 주소를 가리키도록 변경되는데, 메모리에는 '문자열1'과 '문자열2'가 모두 남아있게 된다.


### 4.3 템플릿 리터럴
ES6부터 템플릿 리터럴 이라고 하는 새로운 표기법이 도입되었다. 템플릿 리터럴은 멀티라인 문자열, 표현식 삽입, 태그트 템플릿 등 편리한 문자열 처리 기능을 제공한다. 템플릿 리터럴은 런타임에 일반 문자열로 변환되어 처리된다.
템플릿 리터럴은 따옴표가 아닌 백틱(``)을 이용해 표현한다.
```
멀티라인 예제
var template = `
  멀티라인
  테스트
`;
```
일반 문자열로 줄바꿈을 표현하려면 \n 과 같은 이스케이프 시퀀스를 사용해야 한다.



```
표현식 삽입 예제
var template = `1 + 2 = ${1 + 2}`; // 1 + 2 = 3
var str = '1 + 2 = ${1 + 2}'; // 1+ 2 = ${1 + 2}
```
표현식을 삽입하려면 ${}으로 표현식을 감싸면 된다. 이 때 반드시 템플릿 리터럴 안에서만 해야하며, 일반 문자열에서는 문자열로 취급된다.


### 4.4 불리언 타입
불리언(boolean) 타입은 논리적 참, 거짓을 나타내는 true와 false 밖에 없다.


### 4.5 undefined 타입
undefined 타입은 undefined가 유일하다. var 키워드로 선언한 변수는 변수 선언에 의해 확보된 메모리 공간을 처음 할당이 이뤄질 때 까지 undefined로 초기화 한다. 따라서 변수를 선언한 이후 값을 할당하지 않은 변수를 참조하면 undefined가 반환된다.
이처럼 undefined는 개발자가 의도적으로 할당하기 위한 값이 아니라 자바스크립트 엔진이 변수를 초기화할 때 사용하는 값이다. 변수를 참조했을 때 undefined가 출력된다면 참조한 변수가 선언 이후 값이 할당되지 않았음을 의미한다.
이러한 변수를 개발자가 의도적으로 변수에 할당한다면 undefined의 본래 취지와 어긋나기 때문에 권장하지 않고, 값이 없다는 것을 명시하고 싶을 때는 undefined가 아닌 null을 할당한다.


### 4.6 null 타입
null 타입은 null이 유일하다. 프로그래밍 언어에서 null은 변수에 값이 없다는 것을 의도적으로 명시할 때 사용하며, 이는 변수가 이전에 참조하던 값을 더 이상 참조하지 않겠다는 의미이다.


### 4.7 심벌 타입
심벌은 ES6에서 추가된 7번째 타입으로, 변경 불가능한 원시 타입의 값이다. 심벌 값은 다른 값과 중복되지 않는 유일무이한 값으로, 주로 이름이 충돌할 위험이 없는 객체의 유일한 프로퍼티 키를 만들기 위해 사용한다.
심벌은 Symbol 함수를 호출해 생성한다. 이때 생성된 심벌값은 외부에 노출되지 않으며, 다른 값과 절대 중복되지 않는 유일무이한 값이다.
```
var key = Symbol('key');
var obj = {};
obj[key] = 'value';
console.log(obj[key]); // value
```


### 4.8 객체 타입
자바스크립트는 객체 기반의 언어이다. **자바스크립트를 이루고 있는 거의 모든 것이 객체**라는 의미로, 위에서 살펴본 6가지 타입 이외에는 모두 객체 타입이다.


### 4.9 데이터 타입의 필요성
자바스크립트의 모든 값은 데이터 타입을 가지며, 메모리에 2진수로 저장된다. 메모리에 저장된 값은 데이터 타입에 따라 다르게 해석될 수 있는데, 메모리에 저장된 값 0100 0001을 숫자로 해석하면 65지만 문자로 해석하면 'A'이다. 즉, 데이터 타입은 값의 종류를 말한다. 데이터 타입이 필요한 이유는 다음과 같다.
 - 값을 저장할 때 확보해야 하는 메모리 공간의 크기를 결정하기 위해
 - 값을 참조할 때 한 번에 읽어 들여야 할 메모리 공간의 크기를 결정하기 위해
 - 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정하기 위해


### 4.10 동적 타이핑
자바스크립트의 모든 값은 데이터 타입을 갖는다. 그렇지만 자바스크립트의 변수는 동적 타입을 갖기 때문에 var, let, const로 변수를 선언할 뿐이지 이 변수에는 어떤 데이터 타입의 값이라도 모두 할당할 수 있다.
자바스크립트에서는 typeof 연산자를 사용하면 변수의 데이터 타입을 반환하는데, 정확히 말하면 변수의 데이터 타입이 아니라 변수에 할당된 값의 데이터 타입을 반환한다.
즉, **자바스크립트의 변수는 선언이 아닌 할당에 의해 타입이 결정되며, 이 타입은 추후 재할당을 통해 언제든 동적으로 변할 수 있다.**
```
foo = {}; // 객체
console.log(typeof foo); // object

foo = []; // 배열
console.log(typeof foo); // object

foo = function () {}; // 함수
console.log(typeof foo); // function
```