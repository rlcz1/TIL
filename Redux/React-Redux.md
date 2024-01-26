### Action
어떠한 변화를 일으킬때마다 액션객체를 생성해야한다.  
매번 작성해야 하는 번거로움을 덜고, 실수를 방지하기 위해 함수로 만들어 관리한다.
- Action은 반드시 type필드를 가지고 있어야 한다.
```javascript
  const Input = text => ({
    type : "Input",
    text
  })
```

### Reducer
상태를 변화시키는 함수이다.  
현재 상태와 만든 액션을 통해 새로운 상태를 만들어 반환한다. 
- Reducer는 상태의 불변성을 유지하며 변화를 주어야 함으로, 아래에서는 Spread Operator(...)를 사용해 기존 state를 복사하여 사용한다.   
Redux는 Reducer를 거친 state가 변경되었는지 확인하기 위해 state 객체의 주소를 비교하는데, 복사하지 않고 속성만 변경해서 반환하면 변경이 감지되지 않기 떄문이다.
```javascript
const Reducer = (state, action) => {
  switch(action.type) {
    case 'INCREASE':
      return {
        ...state,
        counter : state.counter + 1;
      }
    case 'DECREASE':
      return {
        ...state,
        counter : state.counter - 1;
      }
    default:
      return state;
  }
}
```

### Store
상태와 리듀서를 포함하는 객체이다.  
하나의 프로젝트는 하나의 스토어만 가질 수 있다.
```javascript
import { createStore } from 'redux';

(...)

// 파라미터에는 리듀서 함수를 넣어야 한다.
const store = createStore(reducer);
```

### Dispatch
액션을 발생시키는 스토어의 내장 함수 중 하나이다.  
함수 호출시 스토어는 리듀서를 실행하여 새로운 상태를 생성한다.
```javascript
import { createStore } from 'redux';

(...)

// 파라미터에는 리듀서 함수를 넣어주어야 한다.
const store = createStore(reducer);

button.onclick = () => { 
   // dispatch 함수를 사용하여 액션을 스토어에게 전달한다.
   store.dispatch(plus(1));
}
```