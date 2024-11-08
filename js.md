# 자바스크립트 메모

## 이벤트 리스너 추가
```javascript
dom.oneventname = e => {}
dom.addEventListener() // 이 방법을 권장, 이유는 removeEventListener 사용이 가능함
```

## CSS IN JS 
- JS에서 DOM 의 CSS를 제어
```javascript
const h1 = document.querySeletor("div h1:first-child");

function handleTitleClick(){
const clickedClass = "clicked";
  if(h1.classList.contains(clickedClass)){
    h1.classList.remove(clickedClass);
  } else {
    h1.classList.add(clickedClass);
  }
}

//위와 동일한 기능을 하는 코드
//toggle
function handleTitleClick(){
  h1.classList.toggle("clicked");
}

h1.addEventListener("click",handleTitleClick);
```
