## Destructuring assignment
### 비구조화 할당 (구조분해) 문법
객체 안에 있는 값을 추출해서 변수 혹은 상수로 바로 선언 가능.
```javascript
const object = { a: 1, b: 2 };

const { a, b } = object;

console.log(a); // 1
console.log(b); // 2
```
함수의 파라미터에서도 비구조화 할당 가능.
```javascript
  const object = { a: 1, b: 2 };

function print({ a, b }) {
  console.log(a);
  console.log(b);
}

print(object);
```

### 비구조화 할당시 기본값 설정
b가 지정되지 않았다면 undefined
```javascript
const object = { a: 1 };

function print({ a, b }) {
  console.log(a);
  console.log(b);
}

print(object);
// 1
// undefined
```
b의 기본값 지정
```javascript
const object = { a: 1 };

function print({ a, b = 2 }) {
  console.log(a);
  console.log(b);
}

print(object);
// 1
// 2
```
```javascript
const object = { a: 1 };

const { a, b = 2 } = object;

console.log(a); // 1
console.log(b); // 2
```

### 비구조화 할당시 이름 바꾸기
animal.name 값을 nickname 변수에 담으려 할때, 이름이 같다면 비구조화 할당을 쓰는것이 가능하지만 이름이 서로 다르다.

```javascript
const animal = {
  name: '멍멍이',
  type: '개'
};

const nickname = animal.name;

console.log(nickname); // 멍멍이
```
이러한 상황에서는 `:`문자를 사용해서 이름을 바꿔줄 수 있음.
```javascript
const animal = {
  name: '멍멍이',
  type: '개'
};

const { name: nickname } = animal
console.log(nickname);
```
'animal 객체 안에 있는 name 을 nickname 이라고 선언하겠다.' 라는 의미