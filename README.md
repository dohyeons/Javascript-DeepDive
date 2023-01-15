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
개발자 도구에서 표현식이 아닌 문을 실행하면 언제나 undefined를 출력하는데, 이를 **완료 값**이라고 한다. 완료값은 평과 결과가 아니라 할당할 수 없고, 참조할 수 없다.