<template>
  <div class="slider-wrapper">
    <div
      class="slider"
      :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
    >
      <div v-for="(slide, index) in slides" :key="index" class="slider-item">
        <div
          class="slider-image"
          :style="{ backgroundImage: `url(${slide.image})` }"
        ></div>
        <div class="slider-info">
          <p class="typography-text-xs md:typography-text-sm font-bold tracking-widest text-neutral-500 uppercase">
            Feel the music
          </p>
          <h1 class="typography-display-2 md:typography-display-1 md:leading-[67.5px] font-bold mt-2 mb-4">
            New Wireless Pro
          </h1>
          <p class="typography-text-base md:typography-text-lg">
            Spatial audio. Adjustable ear cups. On-device controls. All-day
            battery.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 mt-6">
            <SfButton class="custom-button" size="lg"> Order now </SfButton>
            <SfButton size="lg" variant="secondary" class="bg-white custon-button secondary">
              Show more
            </SfButton>
          </div>
        </div>
      </div>
    </div>
    <div class="slider-dots">
      <span
        v-for="(slide, index) in slides"
        :key="index"
        class="dot"
        :class="{ active: index === currentSlide }"
        @click="goToSlide(index)"
      ></span>
    </div>
  </div>
</template>

<script>
import { SfButton } from "@storefront-ui/vue";

export default {
  components: {
    SfButton,
  },
  data() {
    return {
      currentSlide: 0,
      slides: [
        {
          image: "https://alikinvv.github.io/svg-mask-slider/img/1.jpg",
          title: "Slide 1",
          description: "Description for Slide 1",
        },
        {
          image: "https://alikinvv.github.io/svg-mask-slider/img/2.jpg",
          title: "Slide 2",
          description: "Description for Slide 2",
        },
        {
          image: "https://alikinvv.github.io/svg-mask-slider/img/1.jpg",
          title: "Slide 3",
          description: "Description for Slide 3",
        },
      ],
      timer: null,
    };
  },
  mounted() {
    this.startSlider();
  },
  methods: {
    startSlider() {
      this.timer = setInterval(this.nextSlide, 3000);
    },
    stopSlider() {
      clearInterval(this.timer);
    },
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.slides.length;
    },
    goToSlide(index) {
      this.currentSlide = index;
      this.stopSlider();
      this.startSlider();
    },
  },
  beforeDestroy() {
    this.stopSlider();
  },
};
</script>

<style scoped>
.slider-wrapper {
  position: relative;
  width: 100%;
  max-width: 100%;
  margin: 0 auto;
  overflow: hidden;
  height: 60vh;
}

.slider {
  display: flex;
  transition: transform 0.5s ease-in-out;
  height: 100%;
}

.slider-item {
  min-width: 100%;
  position: relative;
  height: 100%;
}

.slider-image {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
}

.slider-info {
  position: absolute;
  bottom: 20%;
  left: 5%;
  color: #fff;
  padding: 10px;
  border-radius: 5px;
}

.slider-info p {
  font-size: 14px;
}

.slider-info h1 {
  font-size: 24px;
}

.slider-info .typography-text-base {
  font-size: 16px;
}

.slider-info .typography-display-2 {
  font-size: 30px;
}

.slider-info .typography-display-1 {
  font-size: 44px;
}

.slider-dots {
  position: absolute;
  bottom: 10px;
  width: 100%;
  display: flex;
  justify-content: center;
}

.dot {
  height: 10px;
  width: 10px;
  margin: 0 5px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  cursor: pointer;
  transition: background-color 0.3s;
}

.dot.active {
  background-color: #717171;
  border: 1px solid black;
}

@media (max-width: 900px) {
  .slider-wrapper {
    height: 50vh;
  }

  .slider-info {
    bottom: 15%;
    left: 5%;
  }

  .slider-info p {
    font-size: 12px;
  }

  .slider-info h1 {
    font-size: 20px;
  }

  .slider-info .typography-text-base {
    font-size: 14px;
  }

  .slider-info .typography-display-2 {
    font-size: 26px;
  }

  .slider-info .typography-display-1 {
    font-size: 36px;
  }
}

@media (max-width: 440px) {
  .slider-wrapper {
    height: 40vh;
  }

  .slider-info {
    bottom: 10%;
    left: 5%;
    width: 50%;
  }

  .slider-info p {
    font-size: 10px;
  }

  .slider-info h1 {
    font-size: 16px;
  }

  .slider-info .typography-text-base {
    font-size: 12px;
  }

  .slider-info .typography-display-2 {
    font-size: 22px;
  }

  .slider-info .typography-display-1 {
    font-size: 28px;
  }

  .slider-info .custom-button{
    display: none;
  }
}
</style>
