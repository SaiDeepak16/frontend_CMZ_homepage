<template>
    <div class="banner1">
      <div class="makeitbold">MAKE IT BOLD</div>
      <div class="content">
        <p>Choose the products you require at the prices you deserve, Never settle at <span>any cost</span></p>
        <div class="arrow">
          <svg xmlns="http://www.w3.org/2000/svg" width="157" height="16" viewBox="0 0 157 16" fill="none">
            <path
              d="M156.71 8.70711C157.101 8.31658 157.101 7.68342 156.71 7.29289L150.346 0.928932C149.956 0.538408 149.323 0.538408 148.932 0.928932C148.542 1.31946 148.542 1.95262 148.932 2.34315L154.589 8L148.932 13.6569C148.542 14.0474 148.542 14.6805 148.932 15.0711C149.323 15.4616 149.956 15.4616 150.346 15.0711L156.71 8.70711ZM0 9H156.003V7H0V9Z"
              fill="black" />
          </svg>
          <span> BUY NOW</span>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  </script>
  
  <style scoped>
  .banner1 {
    background-image: radial-gradient(#939393 1px, transparent 1px);
    background-size: 10px 10px;
}

.banner1 .makeitbold {
    font-size: 11vw;
    font-weight: 800;
    letter-spacing: .1em;
    display: flex;
    justify-content: center;
    align-items: center;
    background-image: url(../images/textBg.png);
    background-size: cover;
    background-clip: text;
    color: transparent;
}

.banner1 .content {
    width: 100%;
    display: flex;
    place-items: center;
    justify-content: space-between;
    padding: 1% 6%;
    box-sizing: border-box;
}

.banner1 .content p {
    font-size: 1.4vw;
    font-weight: 300;
    width: 40%;
}

.banner1 .content p span {
    font-weight: 500;
    font-size: 1.6vw;
}

.banner1 .content .arrow {
    margin-right: 3%;
}

.banner1 .content .arrow span {
    font-size: 2.2vw;
    margin-left: 1vw;
    font-weight: 700;
}


  </style>
  