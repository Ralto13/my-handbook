# basic

## basic 1
타입스크립트에서 변수에 타입을 명시
```typescript
// 타입 추론이 되는형태로 사용하지 않아도 됨
let num: number = 1
let str: string = 'asdf'
```

## basic 2
### 선택적 변수
- ?:로 타입명시하고 프로퍼티의 값이 선택적
```typescript
const player : {
  name:string,
  age?:number
} = {
  name:"jack"
}
// 에러
if(player.age < 10) {

}

// 단축평가 한 경우 에러 없음
if(player.age && player.age < 10) {

}
```

### 타입별칭, 함수 인자, 반환
```typescript
type Name = string;
type Age = number;
type Player = {
  name:Name,
  age?:Age
}

const playerMaker = (name:string): Player => ({name})
const nico = playerMaker("nico")
nico.age = 12
```

### readonly
배열이나 객체속성을 읽기전용으로 지정
```typescript
const names: readonly string[] = ["1","2"]
type player = {
  readonly name:string,
  age?:number
}
```

### any
아무 타입이나 가능하고 타입스크립트의 보호를 받지 않는 타입
```typescript
let a: any[] = [1,2,3]
let b: any = true
a + b
```

### unknown
아무 타입이나 가능하고 타입스크립트의 보호를 받는 타입
- API 데이터 사용 시 사용됨
```typescript
let a:unkown;

if(typeof a === 'number'){
  let b = a + 1
}

if(typeof a === 'string'){
  let b = a.toUpperCase()
}
```

### void && never
- void
  - 함수 리턴값 지정하지 않음
- never
  - 타입이 없는 경우
  - 에러를 반환할 때 사용됨
```typescript
//void
function hello() {
  console.log('x')
}
//never
function unknownColor(x: never): never {
    throw new Error("unknown color");
}


type Color = 'red' | 'green' | 'blue'

function getColorName(c: Color): string {
    switch(c) {
        case 'red':
            return 'is red';
        case 'green':
            return 'is green';
        default:
            return unknownColor(c); // 'string' 타입은 'never' 타입에 할당할 수 없음
    }
}
```

## basic 3
### call signatures
- 에디터에서 함수의 인자, 반환타입을 알려줌
- 타입 지정하지 않아도 타입을 알려줌
- 프로그램을 작성하기 전 타입을 먼저 생각하고 코드를 구현하는 방식에서 쓰임
```typescript
type Add = (a:number,b: number) => number
const add:Add = (a,b) => a+b;
```

### Overloading
- 함수가 여러개의 call signatures를 가진 경우 발생
- Nextjs에서 함수인자 타입을 문자열과 객체로 받을 수 있는것을 볼 수 있음
```typescript
//객체를 넘기는 경우
router.push({
  path:"/home",
  state:2
})
//문자열을 넘기는 경우
router.push("/home")
```

- 위 라우터를 예시로 오버로딩한 코드
```typescript
type Config = {
  path: string,
  state: object
}

type Push = {
  (path:string):void
  (config:Config):void
}

// Push type alias 로 오버로딩
const push:Push = (config) => {
  if(typeof config === "string") // something code ... 
  else {
    //something code ...
  }
}
```

### Polymorphism
- 타입을 위한 다양성

#### generic
- 함수
```typescript
// 보통 사용하게 될 제네릭
function superPrint<T>(a: T[]){
  return a[0]
}

// 제네릭 타입정의
type Player<E> = {
  name: string
  extraInfo: E
}

type NicoExtra = {
  favFood:string
}

type NicoPlayer = Player<{favFood:string}>

// const nico:Player<NicoExtra> = {
const nico:NicoPlayer = {
  name:"nico",
  extraInfo: {
    favFood: "kim"
  }
}

const lynn: Player<null> = {
  name:"lynn",
  extraInfo:null
}

```