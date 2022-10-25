# this

vue 프레임워크에서 많이 사용된다

this: 어떠한 object를 가리키는 키워드(java에서의 this와 python에서의 self는 인스턴스 자기자신을 가리킴)

함수가 **어떻게 호출**되었냐에 따라 this가 달라진다.

전역문맥에서의 this

함수문맥에서의 this: 함수의 호출방식에 따라

-   단순 호출
-   Method(객체의 메서드로서) ex\_ .method()로 호출
-   Nested

---

## 전역문맥에서의 this

this: window

## 함수문맥에서의 this

정해져 있지 않다.  
함수를 호출한 방법에 의해 결정된다.

### 1\. 단순 호출

this == 전역 객체 (브라우저에서 window, node/js에서는 global)

### 2\. Method

메서드로 선언하고 호출한다면, 객체의 메서드이므로 해당 객체가 바인딩

```
const myObj = {

  data: 1,

  myFunc() {
    console.log(this) // myObj
    console.log(this.data) // 1
  }
}
```

### 3\. Nested(Function 키워드)

#### Function 키워드 사용

```
const myObj = {
      numbers: [1];
      myFunc() {
        console.log(this) // myObj
        this.numbers.forEach(function (number) {
          console.log(number) // 1
          console.log(this) // window
        })
      }
    }
myObj.myFunc()
```

console.log(this) // window 가 아닌 myObj여야 알맞음.  
이를 해결하기 위한게 화살표 함수이다.

#### 화살표 함수 사용

```
const myObj = {
      numbers: [1];
      myFunc() {
        console.log(this) // myObj
        this.numbers.forEach((number) => {
          console.log(number) // 1
          console.log(this) // myObj
        })
      }
    }

myObj.myFunc()
```

화살표 함수에서 this는 자신을 감싼 정적 범위  
자동으로 한 단계 상위의 scope의 context를 바인딩한다.

\=⇒ this를 사용하려면 화살표함수로 맞춰서 사용해야 한다. 기능상의 차이는 없다.

화살표함수는 어디에 선언했는지가 중요하다.

---

### addEventListner의 콜백 함수

addEventListner의 콜백함수는 특별하게 function 키워드의 경우 addEventListner 를 호출한 대상 (event.target)을 뜻함.

반면 화살표 함수의 경우 상위 스코프를 지칭하기 때문에 window 객체가 바인딩 됨

결론 addEventListner의 콜백함수는 function 키워드를 사용해야 한다.

\===⇒ this를 사용할 때는 기본적으로 화살표함수를 사용.

예외적으로 addEventListner는 콜백함수를 function키워드를 사용한다

#### function 키워드 사용

```
    const formTodo = function (event) {
      console.log('formTodo')
      console.log(`this = ${this} / event.target = ${event.target}`)
    }
    
    const formTag = document.querySelector('form')
    
    formTag.addEventListener('click', formTodo)
```

**event 시 결과**

formTodo  
this = \[object HTMLFormElement\] / event.target = \[object HTMLParagraphElement\]

\=> this: 자기자신을 출력함 - 객체 내에 존재

#### 화살표 함수 사용

```
    const formTodo = (event) => {
        console.log('formTodo')
        console.log(`this = ${this} / event.target = ${event.target}`)
    }
     
    const formTag = document.querySelector('form')
    
    formTag.addEventListener('click', formTodo)
```

**event 시 결과**

formTodo  
this = \[object Window\] / event.target = \[object HTMLParagraphElement\]

\=> this: window  
화살표 함수로 바꾸자 this가 window로 바뀌었다.  
화살표함수는 객체 내에 있을 때는 지양하는 것이 좋다. 화살표함수를 사용하면 상위 객체를 지칭하게 됨  
객체의 메서드에서 this 에 접근할 때는 화살표 함수 사용을 지양해야 한다  
( 화살표 함수에서 this 는 한 단계 상위 객체를 참조하기 때문에)

---

#### this가 호출되는 순간에 결정되는 것(런타임) 장점/단점

장점

-   함수(메서드)를 하나만 만들어서 여러 객체에서 재사용할 수 있다.

단점

-   이러한 유연함이 실수로 이어질 수 있다는 것은 단점