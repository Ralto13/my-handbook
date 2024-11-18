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
