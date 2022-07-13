---
layout: single
title: 자바스크립트로 Ghost-Rain 만들기
---

## 고스트레인에 내가 추가한 기능!  
<u> start버튼 누르면 게임 시작 </u>   
<u> timer 생성하기  </u>. 
  

```javascript 
let time = 10;  //시간 설정하는 변수 생성
let startBtn = document.getElementById("startBtn");

startBtn.addEventListener("click", () => {
  startBtn.disabled = true;    // start 버튼 누른 후 다시 못눌리게 비활성화!!
  let interval = setInterval(() => {
    createGhost();
  }, 3000);
  setInterval(() => {  // 1초씩 감소되는 타이머 설정
    if (time >= 0) {   //  time이 0초 이상일때 실행되는 함수
      const timer = document.getElementById("timer");
      const minutes = Math.floor(time / 60);       // time을 60으로 나누면 분이 나온다 딱 안떨어질수도 있으니 Math.floor()사용!
      const seconds = String(time % 60).padStart(2, "0");  // 예를들어 6초면 00:06 으로 padStart사용(아래 부연설명)

      timer.innerText = minutes + ":" + seconds;
      time -= 1;
      console.log(time);
    } else if (time < 0) {
      document.getElementById("timer").innerText = "GAME OVER";
      clearInterval(interval);  // createGhost 종료
    }
  }, 1000); 
});
``` 

- padStart() 

ES8(ES2017)에 새롭게 추가된 기능이다. pad는 좌우에 특정 문자열을 채우는 기능이다.  
```javascript 
const number = 10;
const size = 4;
const result = String(number).padStrt(size, 0); // size는 4여서 네자리를 채움

console.log(result);
// 0010
```



