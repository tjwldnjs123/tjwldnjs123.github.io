---
layout: single
title: 자바스크립트로 Ghost-Rain 만들기
---

## 고스트레인에 내가 추가한 기능!  
<u> start버튼 누르면 게임 시작 </u>   
<u> timer 생성하기  </u>. 
  

```javascript 
let time = 10;
let startBtn = document.getElementById("startBtn");

startBtn.addEventListener("click", () => {
  startBtn.disabled = true;
  let interval = setInterval(() => {
    createGhost();
  }, 3000);
  setInterval(() => {
    if (time >= 0) {
      const timer = document.getElementById("timer");
      const minutes = Math.floor(time / 60);
      const seconds = String(time % 60).padStart(2, "0");

      timer.innerText = minutes + ":" + seconds;
      time -= 1;
      console.log(time);
    } else if (time < 0) {
      document.getElementById("timer").innerText = "GAME OVER";
      clearInterval(interval);
    }
  }, 1000);
});
```

