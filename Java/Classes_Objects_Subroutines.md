# Classes, Objects, and Subroutines
## 내장 서브루틴과 함수
- 서브루틴
  - 특정 작업을 수행하는 명령 집합
  
  - System.exit(0);
    - System 클래스의 exit 서브루틴을 호출하여 프로그램을 종료
    - 매개변수 0은 정상 종료를 의미
    - ```클래스명.서브루틴명(매개변수)``` 형태로 사용
- 함수
  - 값을 반환하는 서브루틴

## 서브루틴과 함수의 정의

### 서브루틴(Subroutine)
- **정의**: 특정 작업을 수행하는 명령 집합
- **목적**: 특정 작업을 수행하도록 설계됨
- **특징**: 
  - 작업 수행 후 값을 반환하지 않음 (void)
  - 단순히 작업만 수행
- **예시**: `System.exit(0)`, `System.out.print()`

### 함수(Function)
- **정의**: 값을 반환하는 서브루틴
- **목적**: 데이터 값을 계산하거나 검색
- **특징**:
  - 작업 수행 후 결과값을 반환
  - 반환된 값은 프로그램에서 활용 가능
- **예시**: `Math.sqrt(x)`, `Math.random()`

### 차이점
| 구분 | 서브루틴 | 함수 |
|------|----------|------|
| 반환값 | 없음 (void) | 있음 |
| 용도 | 작업 수행 | 값 계산/검색 |
| 사용법 | 단독 호출 | 표현식에서 사용 |

## 주요 개념
### 서브루틴의 특징
- **블랙박스**: 내부 동작을 모르고도 사용 가능
- **클래스/객체 포함**: 모든 서브루틴은 클래스나 객체에 포함됨
- **정적 멤버**: `static` 키워드로 표시되는 클래스의 멤버

### 호출 방법
- **형태**: `클래스명.서브루틴명(매개변수)`
- **예시**: `System.exit(0)`, `Math.sqrt(x)`

## 사용 예시
```java
// 함수 호출 시 주의사항
Math.sqrt(x); // 잘못된 사용 - 반환값을 사용하지 않음
System.out.print(Math.sqrt(x)); // 올바른 사용
double result = Math.sqrt(x); // 변수에 저장
```