# Nextjs
- React 프레임워크
- webpack 번들러를 사용
- 모든 컴포넌트는 서버에서 pre render가 된다.
  - use client 사용한 컴포넌트 포함

## Componenet
### server component
- nextjs의 기본 컴포넌트
- js동작 없이 서버에서 랜더링이 된다
- 하위 컴포넌트로 server, clinet component를 가질 수 있다.

### client component
- 코드 최상단에 use client로 client component 임을 선언
- hydration 과정을 거쳐 react 기능을 수행
- 하위컴포넌트로 client component 만 가질 수 있다.

#### react hydration
- 최초 html 렌더링 후 react app으로 초기화 하는 과정
- pre render 후 js를 실행, 이후 인터랙션 가능

### Nextjs의 렌더링
1. 최초 방문 시 server side rendering이 됨 (SSR)
2. 모든 것이 pre render 되어 html로 변환되고 응답
3. client component만이 hydatation 과정을 거침 (CSR)
