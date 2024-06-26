## reduce()
배열의 각 요소를 순회하며 callback함수의 실행 값을 누적하여 하나의 결과값을 반환.
```javascript
arr.reduce(callback[, initialValue])
// 배열.reduce(callback(누적값, 현재값, 인덱스, 요소), 초기값);
arr.reduce(callback(accumulator, currentValue, index, array), initialValue);
```
### 파라미터
**callback function**  
다음 4가지의 인수를 가진다.
1. accumulator - accumulator는 callback함수의 반환값을 누적합니다.
2. currentValue - 배열의 현재 요소
3. index(Optional) - 배열의 현재 요소의 인덱스
4. array(Optional) - 호출한 배열

callback함수의 반환 값은 accumulator에 할당되고 순회중 계속 누적되어 최종적으로 하나의 값을 반환합니다.

**initialValue(Optional)**  
최초 callback함수 실행 시 accumulator 인수에 제공되는 값, **초기값을 제공하지 않을경우 배열의 첫 번째 요소를 사용**하고, 빈 배열에서 초기값이 없을 경우 에러가 발생합니다.

