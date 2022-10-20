|   | **JavaScript** | **Python** |
| --- | --- | --- |
| 들여쓰기 | 2칸 | 4칸 |
| 코드블럭 | {} 중괄호 내부를 의미   : 중괄호를 사용해 코드블럭을 구분한다.      if (조건문) {     console.log('')   } | 들여쓰기를 의미   : 들여쓰기를 사용해 코드블럭을 구분한다.      if 조건문 :       print('') |

#### \[참고\] 코드 스타일 가이드

Aribnb JavaScript Style Guide

[https://github.com/tipjs/javascript-style-guide](https://github.com/tipjs/javascript-style-guide)

 [GitHub - tipjs/javascript-style-guide: Airbnb JavaScript 스타일 가이드 한국어

Airbnb JavaScript 스타일 가이드 한국어. Contribute to tipjs/javascript-style-guide development by creating an account on GitHub.

github.com](https://github.com/tipjs/javascript-style-guide)

### 주석

**한 줄 주석 //**

// 주석

**여러 줄 주석 / \* \*/**

/\*

주석

주석

\*/

## 식별자

: 변수를 구분할 수 있는 변수명

\- 식별자는 문자, 달러($), 밑줄(\_)로 시작

\- 대소문자구분, 클래스명 외에는 소문자로 시작

\- **카멜 케이스**: 변수, 객체, 함수에 사용 ex) nctDream

\- **파스칼 케이**스: 클래스, 생성자에 사용 ex) NctDream

\- **대문자 스네이크 케이스**: 상수(값이 바뀌지 않음)에 사용 ex) NCT\_DREAM

## 변수 선언 키워드

: 변수를 만들 때 키워드를 작성해야 한다. 변수에 기능이 존재하기 때문

1\. let : 블록 스코프 지역 변수를 선언 (추가로 동시에 값을 초기화)

2\. const: 블록 스코프 읽기 전용 상수를 선언 (추가로 동시에 값을 초기화)

3\. var: 변수를 선언 (추가로 동시에 값을 초기화)

#### 변수 선언, 할당, 초기화

\- **선언**: 변수를 생성하는 행위 또는 시점

\- **할당**: 선언된 변수에 값을 저장하는 행위 또는 시점

\- **초기화**: 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점

```
let foo // 선언
console.log(foo) // undefined

foo = 11 // 할당
console.log(goo) // 11

let bar = 0 // 선언+할당
console.log(bar) // 0
```

#### 블록 스코프

파이썬에서의 이름공간

if, for, 함수 등의 중괄호({}) 내부를 가리킴

블록 스코프를 가지는 변수는 블록 바깥에서 접근 불가능

let x = 1  
  
if (x === 1) {  
  let x = 100   
  console.log(x)  블록스코프 // 100  
}  
  
console.log(x)  블록 바깥 // 1

#### 1\. let

let으로 선언한 변수는 재할당은 가능하나 재선언은 불가능하다.

```
let number = 1 // 선언 및 초기값 할당
number = 2 // 재할당 (가능)

let number = 1 // 선언 및 초기값 할당
let number = 2 // 재선언 (불가능)
```

#### 2\. const

const로 선언한 변수는 재할당이 불가능하며 재선언도 불가능하다.

```
const number = 1 // 선언 및 초기값 할당
number = 1 // 재할당 (불가능)

const number = 1 // 선언 및 초기값 할당
const number = 2 // 재선언 (불가능)
```

선언 시 반드시 초기값을 설정해야 하며,

(const number (초기값 없이 선언 불가능))

이후 값 변경이 불가능하다.

#### 3\. var

var로 선언한 변수는 재할당 가능하며 재선언 가능하다.

ES6 이전에 변수를 선언할 때 사용되던 키워드

**호이스팅** 되는 특성으로 인해 예기치 못한 문제 발생 가능. 따라서 ES6 이후부터는 var 대신 const와 let을 사용하는 것을 권장

**함수 스코프(function scope)**를 가짐

**※ 함수 스코프**

함수의 중괄호 내부를 가리킴

함수 스코프를 가지는 변수는 함수 바깥에서 접근 불가능 

function nct() {

  var x = 23

  console.log(x)   // 함수 스코프

}

console.log(x)   //  함수 바깥 : 접근 불가능. ReferenceError 

**※ 호이스팅**: 변수를 선언 이전에 참조할 수 있는 현상. var로 선언된 변수는 선언 이전에 참조할 수 있으며, 이러한 현상을 호이스팅이라 함

변수 선언 이전의 위치에서 접근 시 undefinded를 반환한다.

console.log(name)  // undefined  - 선언된 후 할당만 되지 않은 상태로 이해하고 참조가 가능해짐

var name = 'mark'

변수를 선언하기 전에 접근이 가능한 것은 코드의 논리적인 흐름을 꺠뜨리는 행위이며 이러한 것을 방지하기 위해 let, const가 추가되었음. 즉 var는 사용하지 않아야 하는 키워드이다.

변수 선언 키워드는 기본적으로 const 사용하며, 재할당해야 하는 경우만 let을 사용한다.