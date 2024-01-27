
## Reducer
### createSlice
- 기존의 **createReducer**와 **createAction**이 하던 일을 한다.
- name은 리듀서 이름이다.
- initialState는 들어갈 데이터의 초기값을 설정한다.
- reducers는 상태가 변하면 어떻게 실행될지 정한다.
   - state는 설정한 초기값의 value를 가져온다.
   - action에는 playload와 type이 있는데, 변경하고자 하는 데이터를 원하는곳에 넘겨주는 역할을 한다.
    ```javascript
    import {createSlice} from "@reduxjs/tookit"

    // reducer사용시 initialState를 자주 작성해야 하기에 분리해준다.
    const initialStateValue = {id: "", email: "", nickname: ""};

    export const userSlice = createSice({
      name: "user",
      initialState: {value: initialStateValue}
      // initialState: {value: {id: "", email: "", nickname: ""}},
      reducers: {
        login: (state, action) => {
          state.value = action.payload
        },
        logout: (state) => {
          state.value = initialStateValue
        }
      },
    });

    // login함수를 action기능이 작동되도록, 다른곳에서 사용한다는 의미.
    export const {login, logout} = userSlice.actions; 

    export default userSlice.reducer;
   ```

## Store
### configureStore
```javascript
import {configureStore} from "@reduxjs/toolkit"
import userReducer from "./user"

export default configureStore({
  reducer: {
    user: userReducer
  }
});
```
## 사용
### useSelector
- useSelector를 이용해 생성한 reducer에 접근 가능하다.

```javascript
import React from "react"
import {userSelector} from "react-redux"

const UserProfile = () => {
  const user useSelector((state) => state.user.value);
  return (
    <>
      <div>id: {user.id}</div>
      <div>nickname: {user.nickname}</div>
      <div>email: {user.email}</div>
    </>
  );
}
```
### useDispatch
- 사용할곳에서 useDispatch를 통해 action을 보낸다.
```javascript
import React from "react"
import {userDispatch} from "react-redux"
import {login} from "../redux/user"

const Login = () => {
  const dispatch = useDispatch();
  return(
    <>
      <button onClick={() => {
        dispatch(
          login({id: "userId", email: "temp@gmail.com", nickname: "사용자1"})
        )
      }}>
       로그인버튼
      </button>

      <button onClick={() => {dispatch(logout()) }}>로그아웃버튼</button>
    </>
  );
}

export default Login;
```