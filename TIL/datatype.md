데이터 타입
1. 원시타입 2. 참조타입으로 분류



1.  원시 타입
1) Number
: 정수 또는 실수형 숫자를 표현하는 자료형



NaN

: Not a Number 숫자가 아님을 나타냄

유형이 Number이고 값이 NaN이면 true, 아니라면 false를 반환한다.



Number.isNaN(0/0) // true : Number이면서 NaN임

Number.isNaN(123) // false: Number이면서 NaN이 아님

Number.isNaN('가나다') // false: Number가 아님



2) String
: 문자열을 표현하는 자료형

곱셈, 나눗셈, 뺄셈은 안되지만 덧셈을 통해 문자열 붙일 수 있음



\n을 사용하여 줄바꿈 사용 가능



※ Template Literal (템플릿 리터럴)

: Python의 f-string과 같은 기능

${  }로 표기한다.



const longitude = 127
const message = `서울의 경도는 ${longitude}입니다.`

console.log(message)





3) Empty Value
값이 존재하지 않음ㅇ르 표현하는 값으로 JavaScript에서는 null과 undefined가 존재



(1) null

null 값을 나타내는 특별한 키워드

변수의 값이 없음을 표현할 때 사용하는 데이터 타입

- null의 타입은 객체(-> 출력상의 버그임. 다른 원시 타입들은 자신이 타입임)



(2) undefined

값이 정의되어 있지 않음을 표현하는 값(선언만 하고 할당하지 않은 변수)





4) Boolean
true와 false. 참과 거짓을 표현하는 값



연산자
할당 연산자
: 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당하는 연산자



※ Increment 연산자(++)

피연산자의 값을 1 증가시키는 연산자

let x = 0

x ++

console.log(x) // 1

※ Decrement 연산자(--)

피연산자의 값을 1 감소시키는 연산자

let x = 0

x --

console.log(x) // -1





비교 연산자
: 피연산자들을 비교하고 결과값을 boolean으로 반환하는 연산자





동등 연산자(==)
: 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 값을 반환

비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교

const a = 123

const b = '123'

console.log(a == b) // true





일치 연산자(===)
두 피연산자의 값과 타입이 모두 같은 경우 true를 반환

같은 객체를 가리키거나, 같은 타입이면서 같은 값인지를 비교

엄격한 비교가 이뤄지며 암묵적 타입 변환이 발생하지 않음

const a = 123

const b = '123'

console.log(a === b) // false





논리 연산자
and 연산 : &&

or 연산: ||

not 연산: !





삼항 연산자
3개의 피연산자를 사용하여 조건에 따라 값을 반환하는 연산자

가장 앞의 조건식이 참이면 :(콜론) 앞의 값이 반환되며, 그 반대일 경우 : 뒤의 값이 반환되는 연산자

삼항 연산자의 결과값이기 때문에 변수에 할당 가능

true ? 123 : 456 // 123

false ? 123 : 456 // 456







