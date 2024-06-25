## useLocation
`React Router` 라이브러리에서 제공하는 훅(hook) 중 하나로, 현재 페이지의 정보를 가져오는데 사용.
```javascript
import { useLocation } from 'react-router-dom';

const MyComponent = () => {
    const location = useLocation();

    return (
        <div>
            <p>Pathname: {location.pathname}</p>
            <p>Search: {location.search}</p>
            <p>Hash: {location.hash}</p>
            <p>Hash: {location.state}</p>
            <p>Hash: {location.key}</p>
        </div>
    );
};
```

현재 url
```
http://example.com/products?category=electronics#top
```

### pathname
현재 url의 경로 부분. 경로는 **호스트 이름**과 **포트 번호 이후**, ***쿼리 파라미터와 해시부분을 제외한 부분***을 의미.  
pathname
```
/product
```
### search
현재 url에서의 쿼리 파라미터. ?로 시작하여 key=value형식을 전달되며, 여러개의 쿼리 파라미터는 &로 구분.  
search
```
?category=electronics
```
### hash
현재 URL에서 해시 부분. 해시 부분은 #로 시작하며, 주로 페이지 내에서 특정 섹션이나 위치를 가리킬 때 사용.
hash
```
#top
```
### state
이 프로퍼티는 라우팅된 컴포넌트로 전달되는 상태 객체를 나타냄. 이전 경로에서 새로운 경로로 이동할 때 상태를 함께 전달하고 싶을 때 사용될 수 있음.

예를 들어, 다른 컴포넌트로부터 전달받은 데이터를 포함할 수 있다.
### key
이 프로퍼티는 라우팅된 위치의 고유한 식별자를 나타냄. React Router는 각각의 라우트 변경에 대해 고유한 키를 생성하여 라우팅된 컴포넌트의 인스턴스를 추적한다.