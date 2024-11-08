1. [자바스크립트](#js-ts)
    1. [표기법](#표기법)
2. [CSS](#css)
    1. [BEM](#bem)

# JS
### 표기법
### 변수, 함수(메소드)
- 카멜
> myVariable, calculateTotal()

### 클래스, 컴포넌트
- 파스칼
> UserProfile, Navbar

### 백엔드 데이터, 환경변수
- 스네이크
> snake_case, SNAKE_CASE

### 디렉토리, URL
- 케밥
> /user-profile, /images/icons/

### 상수 
- 스크리밍 스네이크
> MAX_VALUE, API_URL

### 문자열 상수
- 2번이상 사용된 문자열은 상수로 만든다
- 상수의 변수명은 스크리밍 스네이크 표기법을 사용한다
- 프로그래밍에서의 관습
### 사용하는 이유
- 문자열로 오타가 난 경우 자바스크립트에서 오류를 확인하기 어렵지만 변수명은 오류가 발생하여 권장된다.
```javascript
const HIDDEN_CLASSNAME = "hidden";
```

# CSS
CSS에서 보통 BEM 방법론이 권장되며 케밥케이스와 BEM의 조합으로 CSS에서 사용
### BEM
- BLOCK
  - 독립적으로 사용 가능한 UI 요소, 단일명사로 나타냄
  - button, menu, card 등
- Element
  - Block의 하위 요소이며, 두 개의 밑줄을 사용해 Block과 연결
  - button__icon, card__title 등
- Modifier
  - Block이나 Element의 변형을 나타내며, 두 개의 대시로 구분
  - button--primary, card--highlighted 등
