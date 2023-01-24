# Javascript-DeepDive
다이소 스터디 딥다이브 정리 저장소📖 
# 01장 프로그래밍
## 1.1 프로그래밍이란?
> **💡프로그래밍**: 컴퓨터에게 실행을 요구하는 커뮤니케이션. 즉, ___문제를 명확히 이해하고 그 해결방안을 정의해야함___

사용자에게는

* **문제를 명확히 이해**하고
* **복잡함을 단순하게 분해**하고
* **자료를 정리하고 구분**하며
* **순서에 맞게 행위를 배열**

하는 능력이 요구됨

그러나 가장 중요한 능력은, 컴퓨터의 관점에서 문제를 생각하는 컴퓨팅 사고(Computational Thinking)이다.

> **💡컴퓨팅 사고(Computational Thinking)**: 해결 과제를 작은 단위로 분해하고, 패턴화해서 추출하며, 프로그래밍에서 사용될 모든 개념을 평가가능하도록 정의함

## 1.2 프로그래밍 언어
문제 해결 방법을 수행하는 주체는 컴퓨터 → 기계어로 명령을 전달해야함

따라서, 사람이 이해할 수 있는 문법으로 구성된 프로그래밍 언어로 프로그램을 작성하고, 컴파일러 혹은 인터프리터를 통해 기계어로 번환해줌

> 프로그래밍 언어는 **구문 + 의미**의 조합이다.

## 1.3 구문과 의미
```
const number = '숫자';
console.log(number * number); // NaN
```
프로그래밍 언어에서도 문법과 의미 둘 다 중요하다. 위의 코드는 문법적으로는 문제가 없지만, 의미적으로는 올바르지 않다. number라는 변수에는 숫자가 할당되는 것이 의미적으로 옳다.

문제 해결 방안 역시 프로그래밍 문법을 통해 표현한다. 따라서 프로그래밍 언어 문법도 어긋나지 않고, 요구하는 바를 정확히 수행해야지만이 의미가 있다.

# 02장 자바스크립트의 특징

> 자바스크립트는 개발자가 별도의 컴파일을 하지 않는 **인터프리터 언어** 이다.

| 컴파일러 언어 | 인터프리터 언어 |
| -- | -- |
| 코드 실행 전 컴파일 타임에 코드 전체를 한번에 머신 코드로 변환 후 실행| 런타임에 문 단위로 한줄씩 바이트 코드로 변환한 후 실행 |
| 실행파일 생성 |  실행파일 X |
| 컴파일과 실행 단계가 명시적으로 분리. 컴파일 - 실행 | 인터프리트와 실행단계가 분리 X. 한 줄씩 바이트코드로 변환 후 바로 실행 |
| 컴파일은 단 한번 실행됨 | 코드가 실행될 때마다 인터프리트 과정이 반복 실행됨 |
| 단계가 분리되어 실행속도가 빠름  | 단계가 분리되어있지 않고 반복되어 실행속도가 비교적 느림 |

# 04장 변수
## 변수란 무엇이고 왜 필요한가
* 컴퓨터는 CPU를 사용해 연산하고, 메모리를 사용해 데이터를 저장한다.
> 메모리: 메모리 셀(1 바이트 = 8비트)의 집합체. 각 셀은 고유의 주소를 가지며, 주소는 0부터 시작해 메모리 크기만큼 정수로 표현됨.

컴퓨터는 모든 메모리를 2진수로 처리 → 데이터 종류에 상관 없이 2진수로 저장됨.

예를 들어, 
```
10+20
```

에서 10과 20은 메모리 임의의 위치에 저장되고, CPU는 이 값을 읽어와서 연산한다. 결과인 30역시 메모리의 어딘가에 저장된다.

그러나 결과인 30은 재사용 할 수가 없는 문제가 발생한다. 결과를 재사용하고 싶다면 메모리 공간에 직접 접근해야 하지만, 자바스크립트에서는 개발자의 직접적인 메모리 제어를 허용하지 않는다.

이를 위해서 프로그래밍 언어는 값을 메모리에 저장하고, 다시 불러들여 재사용하기위해 

___변수___

라는 메커니즘을 제공한다.

변수의 정의란

> 💡**변수**: 하나의 값을 저장하기 위해 확보한 **메모리 공간 자체 또는 그 공간을 식별하기 위해 붙인 이름**을 말한다.

다시말해, 변수 = 값의 위치를 가리키는 상징적인 이름이다.

10 + 20의 값을 저장하고 재사용하고 싶다면 다음과 같이 작성할 수 있다.

```
const sum = 10 + 20;
```

10 + 20은 연산으로 30을 만들고, 30은 메모리 공간의 임의의 주소에 저장되는데, 이 주소를 'sum' 이라는 이름으로 식별하는 것이다.

## 4.2 변수의 선언
변수의 사용 전에는 반드시 선언이 선행되어야 한다.

* 변수의 선언 = 변수의 생성이다.

var, let, const 키워드가 변수 선언에 사용된다. (단, var키워드가 가진 후술할 문제점들 때문에 ES6에서 let, const가 도입되었다.)

변수의 선언은 두 단계로 나뉜다.

1. 선언 단계: 변수 이름을 등록하고 자바스크립트에 존재를 알림
2. 초기화 단계: 메모리공간을 확보하고 암묵적으로 undefined를 할당해 초기화.

* 메모리 공간에는 이전에 사용한 값이 남아있을 수 있어서, 초기화를 하지 않으면 해당 쓰레기 값을 불러올 위험이 있다.

## 4.3 호이스팅
```
console.log(test);

var test;
```
자바스크립트는 위에서 설명했다시피 인터프리터 언어이고, 때문에 한줄씩 실행되어 Reference Error가 발생할 것처럼 보인다.
그러나 출력된 값은 undefined이다.

> 💡***변수 선언이 런타임이 아니라 그 이전 단계에서 먼저 발생했기 때문이다.***

**자바스크립트는 런타임 전 소스코드 평가과정에서 모든 선언문을 찾아 먼저 실행한다. 따라서 변수 선언의 위치와 상관없이 변수를 참조할 수 있다.**

즉,

1. 런타임 전 평가과정에서 ``var test`` 가 먼저 실행되어 자바스크립트에 등록된다(= 선언된다).
2. 선언과 동시에, ``test``는 undefined로 초기화 된다.

의 과정을 거치는 것이다. 

이와 같이, 변수의 선언이 마치 스코프의 최상단에서 이루어진 것처럼 작동하는데, 이를 ***호이스팅*** 이라고 한다. 

# 05장 표현식과 문
## 5.1 값
 > **값** =  식이 평가되어 생성된 결과

 평가 = 식을 해석해서 값을 생성하거나 참조하는 것

 ```
 10 + 20
 ```
 위 식은 평가되고 값 30을 생성한다.

 모든 값은 데이터 타입을 가지고, 메모리에 2진수로 저장된다. 값은 데이터 타입에 따라 다르게 해석될 수 있다.

 ## 5.2 리터럴
 리터럴은 값을 생성하는 방법 중 하나이다.

 > **리터럴** = 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용해 값을 생성하는 표기법

 ```
1 // 숫자 리터럴
'hello' // 문자열 리터럴
function () {} // 함수 리터럴
 ```

## 5.3 표현식
> **표현식** = 값으로 평가될 수 있는 문

값으로 평가될 수 있는 문은 모두 표현식임에 주목하자. 

```
100;
```
리터럴은 값을 생성하므로 그 자체가 표현식이다. 

```
let score = 100 + 100;
```
100 + 100 역시 평가되어 값을 생성하므로 표현식이다.

```
score;
```
score역시 참조되고, 200으로 평가되므로 표현식이다.

이를 다시 생각해보면, 표현식과 표현식이 평가된 값은 동등한 관계를 가진다.

> 따라서 문법적으로 값이 위치할 수 있는 자리에는 표현식이 위치할 수 있다.

또한, 표현식은 다른 표현식의 일부로 값을 생성할 수 있다.
```
let score2 = score + 100;
```

## 5.4 문
> **문** = 프로그램을 구성하는 기본 단위이자 **최소 실행 단위**

> **토큰** = 문법적 의미가 있고, 더 이상 나눌 수 없는 코드의 기본적인 요소

```
let score = 100 + 100
//let, score, =, 100, +, 100. ; 모두 토큰이다.
```
자바스크립트에서 볼 수 있는 오류 Unexpected Token 오류. 예상치 못한 언어 구조를 맞이했을 때 발생하는 오류이다.

문은 선언문, 할당문, 조건문, 반복문 등으로 구분할 수 있다.

## 5.5 세미콜론 & 세미콜론의 자동 삽입 기능
세미콜론은 문의 종료를 의미하며, 자바스크립트는 세미콜론의 위치를 파악하고 순차적으로 문을 실행한다. 즉, 문의 종료 = 세미콜론의 등장이다.

그러나 코드블록은 자체 종결성을 가지기 때문에 세미콜론을 붙이지 않는다.

> 그러나, 문의 끝에 붙이는 세미콜론은 옵션이다. 자바스크립트 엔진이 세미콜론 자동 삽입 기능이 있기 때문이다.

다만 세미콜론 사용이 권장되는 분위기이다. 개발자의 의도와, 기능의 의도가 어긋날 수 있기 때문이다.

## 5.6 표현식인 문 & 표현식이 아닌 문

* 표현식인 문 = 값으로 평가될 수 있는 문
* 표현식이 아닌 문 = 값으로 평가될 수 없는 문

둘을 구분하는 가장 간단한 방법은 변수에 할당해보는 것이다.

```
let x ; 
x = 100;
// 표현식인 문

let x = let y;
// 표현식이 아닌 문
```

++ 완료 값
개발자 도구에서 표현식이 아닌 문을 실행하면 언제나 undefined를 출력하는데, 이를 **완료 값**이라고 한다. 완료값은 평가 결과가 아니라 할당할 수 없고, 참조할 수 없다.

# 06장 데이터 타입
자바스크립트의 모든 값은 데이터 타입을 가진다.
총 7개의 데이터 타입을 제공한다. 6개의 원시타입 + 객체타입으로 이루어진다.

|원시타입|설명 |
| -- | -- |
|숫자|숫자.(정수, 실수 구분이 없다.)|
|문자열|'문자열'|
|불리언|true, false|
|undefined|var키워드의 초기화에 사용되는 값|
|null| 값이 없음을 의도적으로 표현하는 값|
|심벌|ES6에서 추가된 타입|

객체 타입 - 객체, 함수, 배열

+ 타입이 궁금하다면 typeof를 통해 알아볼 수 있다.

## 6.1 숫자 타입
자바스크립트에서는 10진수를 위한 데이터타입만을 지원하기에 2진수 8진수 16진수 모두 참조시에 10진수로 해석된다.
```
0o101 === 0x41 // true
```
또한 다음의 값들 또한 표현할 수 있다.

* Infinity: 양의 무한대
* -Infinity: 음의 무한대
* NaN: 산술 연산 불가. Not a Number를 의미한다.

```
(10 / 0) // Infinity
(10 / -0) // -Infinity
```

## 6.2 문자열 타입
텍스트 데이터를 나타내는 데 사용한다.
'', "", ``으로 텍스트를 감싼다.
```
'이렇게';
"이렇게";
`이렇게`;	
```

## 6.3 템플릿 리터럴
멀티라인 문자열, 표현식 삽입, 태그드 템플릿 등 문자열 처리 기능을 가진 문자열 표기법이다.

오로지 백틱만을 사용한다.

* 멀티라인 문자열
```
console.log(`안녕
하세요`);

// 결과물
안녕
하세요
```

* 표현식 삽입
: ${}으로 표현식을 감싸면 평가결과를 문자열로 바꿔 삽입한다.
```
console.log(`1 + 1 은 ${1 + 1} 입니다.`)
// 1 + 1 은 2 입니다.
```
## 6.4 undefined
 undefined 타입의 값은 undefined가 유일하다.
 undefined는 변수를 초기화하는데 사용된다. 즉, 개발자가 임의로 사용한다면 본래 취지에 어긋나며 혼란을 줄 수 있으므로 권장하지 않는다.
 변수에 값이 없음을 명시하고 싶을떄는 **null**을 사용한다.

 ## 6.5 null
 null 타입의 값 또한 null이 유일하다.
 > 값이 없음을 의도적으로 명시한다. 
 즉, null이 할당된 변수는 더이상 이전의 값을 참조하지 않겠다는 의미이다. 따라서 전에 있던 값의 메모리 공간에 대한 가비지 콜렉션이 수행된다.

 ## 6.6 심벌
> 변경이 불가능한 원시 타입의 값

중복이 되지 않는 유일무이한 값이다. 객체의 프로퍼티 값이 중복없이 유일하기 위해 사용한다.

Symbol 함수를 호출해 생성한다. 외부에 노출되지 않으며, 다른 값과 중복되지 않는다.
```
let key = Symbol('key');
let obj = {};
obj[key] = '값임';
```

## 6.7 데이터 타입의 필요성
### 6.7.1 데이터 타입에 의한 메모리 공간 확보와 참조
메모리 값을 저장하기 위해서는 메모리 공간의 크기를 결정해야 한다.
만약 
```
let num = 100;
```
에서 num을 참조하고 싶으면 어떻게 할까? num에 할당된 값은 숫자 타입으므로 8바이트 단위로 읽지 않으면 값이 훼손된다. 이럴 때 자바스크립트 엔진은 num 변수를 숫자 타입으로 인식해 8바이트 단위로 값을 읽어 들인다. 

### 6.7.2 데이터 타입에 의한 값의 해석
그런데 이 100을 어떻게 해석하느냐의 문제가 남아있다.
모든 값은 메모리에 2진수의 나열로 저장된다. 하지만 데이터 타입에 따라 2진수는 다르게 해석될 수 있기 때문에, 데이터 타입에 따라 다르게 해석될 수 있다.
그러나 num에 숫자 타입의 값이 할당되어 있기 때문에, 자바스크립트 엔진은 이 2진수를 숫자로 해석한다.

## 6.8 동적 타이핑
> 정적 타입 언어(c, 자바): 변수 선언 시 데이터 타입을 사전에 선언해야한다.(명시적 타입 선언).

정적 타입 언어는 컴파일 시 타입 체크를 실시하는데, 이를 통과하지 못하면 프로그램의 실행 자체를 막는다. 

자바스크립트는 변수 선언 시 타입을 선언하지 않고, 키워드만을 사용한다. 따라서 타입에 상관없이 자유로운 할당이 가능하다.  다시말해, 자바스크립트의 변수는 선언이 아닌 할당에 의해 타입이 결정된다. 그리고 재할당에 의해 언제든 타입을 바꿀 수 있는데 이를 **동적 타이핑**이라고 하며, 이러한 언어를 **동적 타입 언어**라고 한다. 동적 타입 언어에서는 값에 의해 변수의 타입이 동적으로 결정된다. 

* 동적 타입 언어의 단점
1. 변화하는 변수 값을 추적하기 어려울 수 있다.
2. 값의 확인 전에는 타입을 확신할 수 없다. 즉, 유연성은 높지만 신뢰성은 떨어진다.

* 변수 사용 시 주의사항
1. 꼭 필요한 경우에만 사용
2. 스코프를 최대한 좁게 만들 것
3. 전역 변수는 최대한 사용을 자제할 것
4. 상수를 사용해 변경을 억제
5. 변수 이름은 목적과 의미를 파악할 수 있도록 네이밍 할 것

# 7장 연산자
> 연산자는 하나 이상의 표현식을 대상으로 산술, 할당, 비교, 논리, 타입, 지수 연산을 수행해 하나의 값을 만든다.

## 7.1 산술 연산자
> 피연산자를 대상으로 수학적 계산을 수행해 새로운 숫자 값을 만든다.
불가능할 경우, NaN을 반환한다.

### 7.1.1 이항 산술 연산자
> 2개 이상의 피연산자를 산술 연산해 숫자 값을 만든다.
### 7.1.2 단항 산술 연산자
> 1개의 피연산자를 산술 연산해 숫자 값을 만든다.
++, -- 등

이 연산자들은 위치에 의미가 있다.
* 피연산자 앞에 위치할 경우 값을 먼저 증가시킨 뒤, 다른 연산을 수행한다.

숫자 타입이 아닌 값에 +, -를 사용하면 피연산자를 숫자 타입으로 변환하여 반환한다.
```
let test = '1';
console.log(typeof +test)// 'number'
test = true;
console.log(+test) // 1
```
### 7.1.3 문자열 연결 연산자
>+의 피연산자 중 하나라도 문자열인 경우 문자열 연결 연산자로 동작한다. 
```
(1 + '1'); // '11'
1 + true; // 2
```
개발자의 의도와 상관없이 암묵적으로 타입이 변환됨에 주의해야한다. 이를 **암묵적 타입 변환** 혹은 **타입 강제 변환** 이라고 한다.

## 7.2 할당 연산자
> 우항의 피연산자를 좌항의 변수에 할당한다.

## 7.3 비교 연산자
> Object.is는 예측 가능한 정확한 비교 결과를 리턴한다.
```
Object.is(NaN, NaN) // true
```

## 7.4 삼항 조건 연산자
삼항 조건 연산자는 값으로 평가할 수 있는 표현식인 문이다. 따라서 값처럼 다른 표현식의 일부가 될 수 있다.
```
let test = 10;
let result = test % 2 ? '홀수' : '짝수';
```
수행해야 할 문이 여러개라면 if else 문의 가독성이 더 좋다.

## 7.5 그룹 연산자
>우선순위를 정하기 위한 연산자. ()를 사용해 감싸면 우선순위가 가장 높다.
```
10 * 2 + 10; // 30
10 * (2 + 10); // 24 
```

## 7.6 지수 연산자
> 좌항의 피연산자를 밑으로, 우항의 피연산자를 지수로 거듭제곱한다
```
2 ** 2; // 4
```

## 7.7 연산자의 부수 효과
> 할당 연산자, 증가/감소 연산자, delete연산자는 다른 코드에 영향을 준다.

```
let test = 1;

test++;

console.log(test); // 2

test --;

console.log(test); // 1

let obj = { a: 1};

delete obj.a;

console.log(obj);// {}
```

## 7.8 연산자 우선순위
연산자 우선순위는 모두 기억하기 어렵다. 따라서 ()를 사용하여 명시적으로 조절하는 것이 권장된다.

# 8장 제어문
> 제어문은 조건에 따라 코드블록을 실행하거나 반복 실행할 때 사용한다.

## 8.1 블록문
> 블록문: 0개 이상의 문을 중괄호로 묶은 것(= 코드 블록, 블록)

* 블록문은 하나의 실행 단위이다. 

* 단독 사용이 가능하나 일반적으로는 제어문, 함수 정의에 사용한다.

* 블록문은 자체 종결성을 가지기 때문에 세미콜론을 붙이지 않는다.

```
{
	let five = 5;
	// 이런식으로 사용하는 경우는 거의 없다.
}

function sum(a, b) {
	return a + b;
}
// 이런식으로 함수 정의에 사용되기도 한다.
```

## 8.2 조건문
> 조건문: 주어신 조건식의 평가 결과에 딸 코드 블록의 실행을 결정한다.

자바크립트의 조건문

1. if ...else 문
2. switch문

### 8.2.1 if...else 문
```
if(조건식) {
	// 조건식이 참일때 실행될 코드
} else {
	// 조건식이 거짓일때 실행될 코드
}
```

* 조건식을 Boolean으로 평가되어야한다.

* 만약 조건에 따라 실행될 블록을 늘리고 싶으면 else if 문을 사용한다.

* if와 else 는 2번 이상 사용이 불가능하다.

* 블록 내부의 문이 하나뿐이라면 중괄호를 생략할 수 있다.
```
if(true) return true;
```

* if...else 문은 삼항연산자로 바꿀 수 있다.
<br>삼항 연산자를 사용하는것이 가독성은 좋으나, 조건이 여러개일 경우 if...else의 가독성이 좋다.

### 8.2.2. switch문
> 표현식을 평가하여 그 값과 일치하는 표현식을 가지는 case문으로 실행흐름을 옮긴다.

* switch문의 표현식과 인치하는 case문이 없으면 순서가 default로 이동한다.

* 참/거짓을 따지기보다는 다양한 상황에 따라 실행할 코드 블록을 결정할 때 쓰인다.

```
let age = 19;
let notion;
switch(age) {
	case 19 : notion = '야 나가';
}

console.log(notion); // '야 나가'
```

그러나 switch문에는 되도록이면 break를 써주는 것이 좋다. 다음의 경우를 보면

```
let age = 19;
let notion;
switch(age) {
	case 19 : notion = '야 나가';
	case 20 : notion = '어서오세연!';
  default : notion = '신분증좀 주세연' ;
}

console.log(notion); // '신분증좀 주세연' 
```
`'야 나가'` 이 출력될거라는 예상과 다르게 default의 문이 실행된 것을 볼 수 있다. 이는 코드의 실행은 정상적으로 `case 19`으로 옮겨졌지만, break문이 없어 밑의 case문과 default문을 거치며 실행했기 때문이다. 이처럼 switch문을 탈출하지 못하고 밑의 case와 default를 실행하는 것을 **폴스루**라고 부른다.

break는 코드 블록에서 탈출하는 역할을 한다. 따라서 위는 다음과 같이 쓰여야 한다.
```
let age = 19;
let notion;
switch(age) {
	case 19 : notion = '야 나가';
	break;
	case 20 : notion = '어서오세연!';
	break;
  default : notion = '신분증좀 주세연' ;
}

console.log(notion); // '야 나가'
```

* if...else문으로 해결할 수 있으면 그러는게 좋은, 조건이 너무 많아 가독성에 문제가 있다면 switch문을 사용하는 것이 더 좋을 수 있다.

## 8.3 반복문
> 조건식의 결과가 거짓이 나오기 전까지 코드를 반복해서 실행한다.

* 자바스크립트에서 제공하는 반복문
1. for 문
2. while 문
3. do...while 문

### 8.3.1 for문
> 조건식이 거짓으로 평가될 때까지 코드를 반복 실행한다.

* for문의 변수 선언문, 조건식, 증감식은 옵션이다. 다만, 어떤 식도 선언하지 않으면 코드가 무한 실행된다.
```
for(;;) {
	console.log('무한실행');
}
```
* for문 안의 코드블록에 for문을 또다시 사용할 수 있다. (중첩 for문)

8.3.2 while문
> 조건식이 거짓으로 평가될 때까지 코드를 반복 실행한다. 다만, **반복 횟수가 불명확 할 때 주로 사용한다.**

### 8.3.3 do...while문
> 코드 블록을 먼저 실행한 다음 조건식을 평가한다.

```
let count = 3;
do {
	console.log(count);
	count--;
} while (count > 0);
```

## 8.4 break 문
> 코드 블록을 탈출한다. 다만, **레이블 문, 반복문, switch문 등의 코드 블록을 탈출한다.** 이 외의 블록에서 사용할 경우 SyntaxError가 발생한다.

* 레이블 문은 식별자가 붙은 문이다.
```
sayHello : console.log('안녕');
```
레이블문은 일반적으로 중첩for문을 탈출할 때 외에는 권장하지 않는다.

## 8.5 continue문
> 반복문의 코드 블록 실행을 여기서 멈추고, 증감식으로 실행 흐름을 이동시킨다.

```
let test = 0;

for (let i = 0 ; i < 5 ; i++) {
	if(i < 2) continue;
	test++;
}
console.log(test); // 3
```
i < 2일 경우 `test++`은 실행되지 않고 증감식(`i++`)으로 이동한다. 그 후 i가 2일때부터 `test++`가 실행된다. 이는 밑의 코드와 같다.

```
for (let i = 0 ; i < 5 ; i++) {
	if(i >= 2) test++;
}
```
실행해야 할 코드가 한줄이면 continue보다 가독성이 좋다. 그러나 코드가 길어진다면 continue문을 사용하는 편이 가독성이 좋다.

```
for (let i = 0 ; i < 5 ; i++) {
	if(i < 2) continue;
	test++;
	console.log('가독성이 좋아연');
}

for (let i = 0 ; i < 5 ; i++) {
	if(i >= 2) {
		test++;
		console.log('가독성이 별루에연');
	}
}
```

# 9장 타입 변환과 단축 평가
## 9.1 타입 변환이란 무엇인가
자바스크립트의 모든 값은 타입이 있고, 개발자의 의도에 따라 다른 타입으로 변환할 수 있다. 
* 명시적 타입 변환(= 타입 캐스팅): 개발자가 의도적으로 타입을 변환하는 것
* 암묵적 타입 변환(= 타입 강제 변환): 개발자 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환

```
let num = 10;
// 명시적 타입 변환. toString을 이용해 의도적으로 타입을 변환함
let str = num.toString();
console.log(typeof str, str); // string, 10;

// 암묵적 타입 변환. 문자열 연결 연산자가 새로운 문자열을 생성
str = num + '';
console.log(typeof str, str); // string, 10;

```

* 이때, 기존의 원시 값 `num`은 직접 변경되지 않는다. 타입 변환은 기존 원시값을 이용해 다르 타입의 새 원시값을 생성하는 것이다. 
> 명시적 타입 변환은 변환의 의지가 코드에 명백히 드러난다. 하지만 암묵적 타입 변환의 경우 자동 변환이기 때문에 개발자의 의지가 명백히 나타나는 것은 아니다.
<br>
따라서 암묵적 타입 변환이 일어나지 않도록 코드를 작성하는 것이 좋다고 생각할 수 있다. 그러나 이는 옳지 않다. 개발자의 입장에서 `(10).toString()`보다는 `10 +''`가 더 간결하고 이해하기 쉽다.
<br>
코드를 작성할 때 가장 중요한 것은 협업을 해야함을 잊지 않는 것이다. 따라서 동료가 쓴 코드를 이해할 수 있어야 하고, 내가 쓴 코드를 동료가 이해하기 쉽도록 해야 한다.

## 9.2 암묵적 타입 변환
자바스크립트에서는 가능한 에러를 줄이기 위해 암묵적 타입 변환을 통해 표현식을 평가한다.
```
'10' + 3 // '103'
```
암묵적 타입 변환이 발생하면 원시 타입 중 하나로 값을 자동 변환한다.

### 9.2.1 문자열 타입으로 변환
> `+` 연산자는 피연산자 중 하나라도 문자열이라면 문자열 연결 연산자로 동작한다.

그 뿐 아니라, 표현식을 평가할때 또한 암묵적으로 타입 변환한다.
```
1 + '2' // -> "12"

//표현식을 암묵적으로 변환한다.
`1 + 1 = ${1 + 1}` // -> "1 + 1 = 2"

```

### 9.2.2 숫자 타입으로 변환
> 산술 연산자 표현식을 평가하기 위해 피연산자 중 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다.

만약 피연산자가 숫자 타입으로 변환이 불가능한 경우, 표현식의 평가 결과는 NaN이 된다.

```
1 - '1' // 0
1 / 'one' // NaN
```

> 비교 연산자 또한 피연산잘르 숫자 타입으로 암묵적 타입 변환한다.

```
1 > '0' // true
```

> `+`단항 연산자는 피연산자가 숫자 타입이 아니면 숫자 타입으로 암묵적 타입 변환한다.
```
// 문자열 타입
+''       // -> 0
+'0'      // -> 0
+'1'      // -> 1
+'string' // -> NaN. string은 숫자 타입으로 평가될 수 없으므로 NaN.

// 불리언 타입
+true     // -> 1
+false    // -> 0

// null 타입
+null     // -> 0

// undefined 타입. 단, 이 경우 NaN을 반환한다. 
+undefined // -> NaN
```
### 9.2.3 불리언 타입으로 변환
> 조건식에서 자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy 값, 또는 Falsy 값으로 평가한다.

Falsy로 평가되는 값은 다음과 같다.

* false
* undefined
* null
* 0, -0
* NaN
* ''

이 외에는 모두 Truthy로 평가된다.

## 9.3 명시적 타입 변환
표준 빌트인 생성자 함수에서 new 연산자 없이 호출, 빌트인 메서드 사용, 암묵적 타입 변환 이용

### 9.3.1 문자열 타입으로 변환
* String 생성자를 new 없이 호출 
* Object.prototype.toString 메서드 사용
* 문자열 연결 연산자 이용

```
// 1. String 생성자 함수를 new 연산자 없이 호출
// 숫자 타입 => 문자열 타입
String(1); // -> "1"
String(NaN); // -> "NaN"
String(Infinity); // -> "Infinity"
// 불리언 타입 => 문자열 타입
String(true); // -> "true"

// 2. Object.prototype.toString 메서드를 사용
// 숫자 타입 => 문자열 타입
(1).toString(); // -> "1"
(NaN).toString(); // -> "NaN"
(Infinity).toString(); // -> "Infinity"
// 불리언 타입 => 문자열 타입
(true).toString(); // -> "true"

// 3. 문자열 연결 연산자를 이용
// 숫자 타입 => 문자열 타입
1 + ''; // -> "1"
NaN + ''; // -> "NaN"
Infinity + ''; // -> "Infinity"
// 불리언 타입 => 문자열 타입
true + '';     // -> "true"
```
### 9.3.2 숫자 타입으로 변환
* Number 생성자 합수 new 연산자 없이 호출
* parseInt, parseFloat함수 사용
* `+` 단항 산술연산자 사용
* `*`산술 연산자 사용

```
// 1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 숫자 타입
Number('0'); // -> 0
// 불리언 타입 => 숫자 타입
Number(true); // -> 1

// 2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
// 문자열 타입 => 숫자 타입
parseInt('0');       // -> 0

// 3. + 단항 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
+'0';     // -> 0
+'-1';    // -> -1
// 불리언 타입 => 숫자 타입
+true;    // -> 1

// 4. * 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
'0' * 1;     // -> 0
// 불리언 타입 => 숫자 타입
true * 1;    // -> 1
```

### 9.3.3 불리언 타입으로 변환
* Boolean 생성자 함수를 new 연산자 없이 호출
* ! 부정 논리 연산자를 두번 사용

```
Boolean('x') // true
Boolean('') // false
Boolean('false') // true

!!'' ; false
!!'false' ; true
```

## 9.4 단축 평가
### 9.4.1 논리 연산자를 사용한 단축 평가
> 논리합, 논리곱 연산자 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.

둘다 좌항에서 우항으로 진행된다.

```
'left' && 'right'; // 'right'
'' || 'right' // ''
```

> **논리곱, 논리합 연산자는 피연산자를 타입 변환하지 않고 그대로 반환하는데, 이를 단축 평가라고 한다.**

단축 평가는 if문을 대체할 수 있다.
```
let age = 19;
let messange;

message = (age >= 19) && '어서오세여 손님!';
console.log(message);

// 이는 다음 식과 같다.
if(age >= 19) message = '어서오세여 손님!'

// 또한 다음과 같이 사용할수도 있다.
message = age < 19 || '야 나가';
console.log(message) // '야 나가'
```

단축 평가의 유용한 패턴은 다음과 같다.
* **객체가 가리키키를 기대한 변수가 null, undefined인지를 확인하고 프로퍼티를 참조할 때**
만약 변수의 값이 객체가 아니라 null, undefined인 경우 타입 에러를 발생시키고, 강제적으로 프로그램이 종료된다. 
이때 단축평가를 사용하면 이를 방지할 수 있다.
```
let obj = null;
let value = obj.value // TypeError

// 이를 아래와 같이 쓰면 에러를 방지한다.
let value = obj && elem.value // null
```

* **함수 매개변수에 기본값을 설정할 때**
함수 호출 시 인수를 전달하지 않는다면 undefined가 할당된다. 단축 평가를 사용해 매개변수의 기본값을 설정하면, undefined일때 생성되는 오류들을 방지할 수 있다.

```
function checkAge(age) {
  age = age || '민자';
  return age >= 19 ? '어서오세연 손님!' : '야 나가'
}

checkAge(); // '야 나가'
```
물론 ES6의 매개변수 기본값 설정을 사용하면 더 쉽게 가능하다.
```
function checkAge(age='민자') {
  return age >= 19 ? '어서오세연 손님!' : '야 나가'
}
checkAge(); // '야 나가'
```

### 9.4.2 옵셔널 체이닝 연산자 `?.`
> 좌항의 피연산자가 null, undefined인 경우 undefined를 반환하고, 아니면 우항의 프로퍼티 참조를 이어간다. 

논리곱의 경우 Falsy값이면 좌항의 피연산자를 그대로 반환했다. 하지만 0과 ''의 경우 객체로 평가되는 경우가 있다.

```
let name = '';
let length = name && name.length; // 이름의 길이를 참조하고 싶음
console.log(length) // ''. 즉 이름의 길이를 참조를 못함
```

하지만 옵셔널 체이닝 연산자의 경우 Falsy값 이라도 null, undefined가 아니면 프로퍼티 참조를 이어간다.
```
let name = '';
let length = name?.length;
console.log(length) // 0
```

### 9.4.2 null병합 연산자 `??`
> 좌항의 피연산자가 null, undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다.

변수에 기본값을 설정할 때 유용하다.
```
// Falsy 값인 0이나 ''도 기본값으로서 유효하다면 예기치 않은 동작이 발생할 수 있다.
var foo = '' || 'default string';
console.log(foo); // "default string"

// 좌항의 피연산자가 Falsy값이라도 null, undefined가 아니면 좌항의 피연산자를 반환한다.
let foo = null ?? 'default string';
console.log(foo); // "default string"
var foo = '' ?? 'default string';
console.log(foo); // ""
```

# 10장 객체 리터럴
## 10.1 객체란 무엇인가
> 다양한 타입의 값을 하나의 단위로 구성한 복합적인 자료구조

* 원시값을 제외한 나머지는 모두 객체다.
* 객체는 0개 이상의 프로퍼티로 구성되어 있으며 프로퍼티는 키와 값으로 구성된다.
* 자바스크립트의 모든 값은 프로퍼티 값이 될 수 있다. 자바스크립트는 함수를 일급 객체 취급하므로, 함수도 값이 될 수 있다. 이를 **메서드** 라고 부른다.

이를 다시 정리하자면
* 프로퍼티: 객체의 상태를 나타내는 값
* 메서드: 프로퍼티를 참조하고 조작할 수 있는 동작

## 10.2 객체 리터럴에 의한 객체 생성
자바스크립트는 다양한 객체 생성 방법을 지원한다.
* 객체 리터럴
* Object 생성자 합수
* 생성자 함수
* object.create 메서드
* 클래스

이 중 가장 일반적인 방법은 객체 리터럴을 이용하는 방식이다. 중괄호 내에 0개 이상의 프로퍼티를 정의한다. 변수에 할당되는 시점에 자바스크립트 엔진이 이를 해석해 객체를 생성한다. 만약 프로퍼티를 정의하지 않으면 빈 객체가 생성된다.
```
let product = {
	price: 6000,
	sale: function() {
		this.price = this.price * 0.5
	}
};

product.sale();
product.price;

let obj = {};
```
여기서 객체 리터럴의 중괄호는 코드 블럭이 아님을 주의하자. 때문에 세미콜론을 붙여야한다.

## 10.3 프로퍼티
> 객체는 프로퍼티의 집합이며, 프로퍼티는 키와 값으로 구성된다.

* 프로퍼티 키: 빈 문자열 포함 모든 문자열 또는 심벌 값
* 프로퍼티 값: 자바스크립트에서 사용할 수 있는 모든 값

프로퍼티 키는 식별자 역할을 하지만 식별자 네이밍 규칙을 반드시 지켜야 하는 것은 아니다. 그러나 식별자 규칙을 따르지 않을 경우 반드시 따옴표를 사용해야 한다.
```
let product = {
	price: 6000,
	'made-in': korea
}
```
* 프로퍼티의 동적 생성 또한 가능하다.
```
let product = {
	price: 6000,
	sale: function() {
		this.price = this.price * 0.5
	}
};

product['name'] = '스파클링';
console.log(product); //{ price: 6000, sale: ƒ sale(), name: '스파클링' }
product[''] = '뭐여';
console.log(product);
// {
  price: 6000,
  sale: ƒ sale(),
  name: '스파클링',
  '': '뭐여'
}
```
여기서 주목할 점은 빈 문자열 또한 키로 사용이 가능하다는 점이다. 그러나 이는 키로서 의미가 없으므로 권장되지 않는다.

* 문자열, 심벌 이외의 값을 키로 사용하면 암묵적 타입 변환을 통해 문자열로 변환된다.

* 예약어를 사용해도 오류가 발생하지는 않는다. 다만 어떤 오류가 생길지 모르니 추천하지는 않는다.

* 같은 키를 사용할 경우 나중에 작성한 키의 값이 먼저 선언한 키의 값을 덮어쓴다.

```
let test1 = {
	0: 0
}

let test2 = {
	function = "function"
}

let test3 = {
	test = "test",
	test = "테스트"
}
```

## 10.4 메서드
> 프로퍼티의 값이 함수일 경우, 일반 함수와 구분하기 위해 메서드라고 부른다. 

## 10.5 프로퍼티 접근 방법
다음의 두가지 방식이 있다.
* 마침표 표기법(. 사용)
* 대괄호 표기법([] 사용) 

프로퍼티 키가 자바스크립트에서 유효한 이름이면 둘 다 사용이 가능하다. 

또한 **대괄호 표기법을 사용하는 경우, 대괄호 내부에는 반드시 따옴표로 감싼 문자열이 들어가야 한다**단, 숫자로 이루어진 문자열이라면 따옴표를 생략할 수 있다.

```
let product = {
	price: 6000,
	sale: function() {
		this.price = this.price * 0.5
	}
};
console.log(product['price']); // 6000
```
객체에 존재하지 않는 프로퍼티에 접근하면 undefined를 반환한다.(ReferenceError가 발생하지 않음에 주의하자.)

* 프로퍼티 키가 자바스크립트에서 유효한 이름이 아니면 반드시 대괄호 표기법을 준수해야한다.

```
let iPhone = {
	'phone-name' : 'iPhone 13',
	13: 'pro'
}
iPhone.'phone-name'; // SyntaxError
iPhone.phone-name; // 브라우저와 Node.js에서의 결과가 다르다.
iPhone['phone-name'] // 'iPhone 13'

iPhone.1; // SyntaxError
iPhone[1]; // 'pro'
```
위에서 브라우저와 Node.js의 실행 결과가 드르다 자바스크립트 엔진에서는 iPhone.phone를 평가한다. 이는 undefined로 평가되며(phone라는 키가 없으니까) 결국 undefined - name과 같아진다.
<br>Node.js에서는 name이라는 식별자가 없으므로 ReferenceError가 발생한다. 하지만 브라우저에는 전역객체에 name이 암묵적으로 존재하는데 이는 빈 문자열이다. 따라서 undefined - ''와 같아져 NaN이 된다.

## 10.6 프로퍼티 값 갱신 및 삭제
> 이미 존재하는 프로퍼티에 값을 할당하면 값이 갱신된다.
```
let person = {
	name: 'do'
}
person.name = 'hs';
console.log(person.name); // 'hs'
```
> delete연산자는 객체의 프로퍼티를 삭제한다. 이때, 존재하지 않는 프로퍼티에 접근하면 에러 없이 무시된다.
```
delete person.name;
delete person.age;
console.log(person); // {}
```

## 10.9 ES6에서 추가된 객체 리터럴 확장 기능
### 10.9.1 프로퍼티 축약 표현
> 변수 이름과 프로퍼티 키가 동일한 이름일 때 프로퍼티 키를 생략할 수 있다.
```
let x = 1;
let y = 2;

let obj = {x, y};
console.log(obj); // {x: 1, y: 2}
```

### 10.9.2 계산된 프로퍼티 이름
> 객체 리터럴 내부에서 프로퍼티 키를 동적 생성할 수 있다. 
```
const prefix = 'test';
let i = 0;

// 객체 리터럴 내부에서 계산된 프로퍼티 이름으로 프로퍼티 키 동적 생성
const obj = {
  [`${prefix}-${++i}`]: i,
  [`${prefix}-${++i}`]: i,
  [`${prefix}-${++i}`]: i
};

console.log(obj); // {test-1: 1, test-2: 2, test-3: 3}
```

### 10.9.3 메서드 축약 표현
> function 키워드를 생략한 축약 표현을 사용할 수 있다.
```
const person = {
	name: 'do',
	sayHi() {
		console.log('안냐세연~~');
	}
}
```