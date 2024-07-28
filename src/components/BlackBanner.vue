<template>
    <div class="banner2">
      <div class="content1">
        {{ title }}
      </div>
      <div class="content2">
        {{ description }}
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: {
        type: String,
        required: true
      },
      description: {
        type: String,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
  .banner2 {
    display: flex;
    justify-content: space-between;
    gap: 2%;
    padding: 5% 4% 5% 5%;
    background: #09090B;
    color: white;
    align-items: center;
}

.banner2 .content1 {
    font-size: 3vw;
    font-weight: 300;
    width: 70%;
    letter-spacing: .01vw;
    line-height: 4vw;
}

.banner2 .content2 {
    width: 50%;
    font-size: 1.4vw;
    font-weight: 200;
}

@media (max-width:440px) {
    .banner2 {
        flex-direction: column;
        gap: 2vh;
        padding: 3% 3%;
    }

    .banner2 .content1 {
        font-size: 4vw;
        text-align: center;
    }

    .banner2 .content2 {
        width: 80%;
        font-size: 1.9vw;
        text-align: center;
    }
}
  </style>
  