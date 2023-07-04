---
title: '404 Not Found！'
comments: false
permalink: /404.html
---

## OOPS! Page Not Found

Sorry, this link is invaild.

It will go back home in <span id="timeout">5</span> s

If you want to read my article, you can **[click here](/en)** to go back home.

<script>
let countTime = 5;

function count() {
  document.getElementById('timeout').textContent = countTime;
  countTime -= 1;
  if(countTime === 0){
    location.href = '/en'; // 記得改成自己網址 Url
  }
  setTimeout(() => {
    count();
  }, 1000);
}

count();
</script>