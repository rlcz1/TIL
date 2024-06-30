## Index Routes
특정 경로에 대한 기본 경로(default route)를 설정하는 방법.  
정확히 일치하지 않는 경로로 접근할 때, 기본 경로를 지정한다.
```javascript
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="dashboard" element={<Dashboard />} />
</Routes>
```
- 위의 코드는 `/` 경로로 접근하면 `<Home />`컴포넌트로 이동하고, `/dashboard` 경로로 접근하면 `<Dashboard />`컴포넌트로 매핑된다.
```javascript
  <Route index element={<Dashboard />} path="dashboard" />
```
- 이 때, index 속성을 추가하여 `/dashboard` 경로에 대한 기본 경로를 설정한다.
- 이제 사용자가 `/dashboard` 경로 이외의 다른 경로로 접근하면 여전히 404페이지로 이동하지만, `/dashboard`경로로 접근할 경우에는 `<Dashboard />`컴포넌트로 매핑된다.
### 중첩된 라우트에서의 index routes 사용
```javascript
<Routes>
    <Route path="/test" element={<Layout />}>
      <Route index element={<MainPage />} />
      <Route path=":movieId" element={<DetailPage />} />
      <Route path="search" element={<SearchPage />} />
    </Route>
  </Routes>

```
- `Layout`을 element로 하는 Route가 나머지 Route를 감싸고있는데, 이 형태는 **부모 컴포넌트 내부에서 자식 컴포넌트 정보에 접근**할 때 쓰는 prop인 `children`을 쓰는것과 유사하다.
```javascript
const Layout = () => {
  return (
    <div>
      <Nav />
      <Outlet />
      <Footer />
    </div>
  );
};
```
- `Layout`안의 `<Outlet />`이 children과 유사하다.
- 예시에서 `<Outlet />`은 `<MainPage />`, `<DetailPage />`, `<SearchPage />`를 의미한다.

## Protected Route
해당 페이지로 이동하기 전에 조건을 명시하여 조건을 만족했을때 해당 페이지로 이동하고, 조건을 만족하지 못했다면 특정 페이지로 돌아가게끔 한다.

Router.js
```javascript
// 작성한 권한 설정 파일 import
import ProtectedRoutes from './ProtectedRoutes'

{/* { 인증을 반드시 하지 않아야만 접속이 가능한 페이지} */}
<Route element={<ProtectedRoutes authentication={false} />}>
  <Route path="/login" element={<Loggin />} />
</Route>

{/* { 인증을 반드시 해야지만 접속 가능한 페이지 } */}
<Route element={<ProtectedRoutes authentication={true} />}>
  <Route path="/test" element={<Testrouter />} />
  <Route path="/counter" element={<Counter />} />
</Route>
```
