# 1. promise 사용해보기(A -> B -> C 출력되도록)
### Promise(콜백 함수)
```javascript
function printSSAFY() {
    return new Promise(function (resolve, reject) {
    setTimeout(() =>{
        console.log('B')
        resolve()  
        // 콜백함수가 정상적으로 동작했는지 판별해주는 기능, 이게 없으면 하단의 .then이 동작하지 않는다(정상적으로 동작했는지 알 수 없기 때문)
    }, 3000)
    })
}
console.log('A')
printSSAFY().then(() =>{
    console.log('C')
})
```
# 2. promise 조금 더 뜯어보기 - promise의 3 가지 상태
### 2.1. pending(대기) 상태
: 비동기 처리 로직이 아직 완료되지 않은 상태
pending 상태 - 만들어놓고 아직 사용하지 않음
```javascript
new Promise()
```


### 2.2.Fullfilled(이행) 상태
잘 동작했다는 걸 표시하기 위해 resolve()를 사용
resolve, reject는 콜백함수
```javascript
const data = new Promise(function (resolve) { 
    resolve(123) // data가 정상적으로 동작하면 resolve안에 있는 내용을 반환한다.
}) 

data.then((value) =>{  // then은 resolve가 반환한 내용을 사용한다.
    console.log(value); 
})
```
### 2.3. Rejected(실패) 상태
비동기 처리가 실패하거나, 오류가 발생한 상태
```javascript
const data = new Promise(function (resolve, reject) {
reject('실패') // 강제로 실패했다를 명시
}) 

// 많이 보게될 코드 구조
// 성공 시 로직 -> 다른 로직 -> 다른 로직
//    -> 하나라도 중간에 실패하거나 오류가 나면 catch 호출
data.then((value) => {
  console.log(value);
  return value
}).then((value) => {
  console.log(value);
  return value
}).then((value) => {
  console.log(value);
  return value
}).catch((error) => {
  console.log(error)
})
```