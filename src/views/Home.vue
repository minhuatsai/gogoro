<template lang="pug">
Header
.home-container
  Carousel(v-bind:carouselList='carouselList')
</template>

<script>
import Header from "../component/header";
import Carousel from "../component/carousel";

export default {
  name: "Home",
  components: { Header, Carousel },
  data() {
    return {
      carouselList: [
        {
          active: true,
          html: `
            <div
              class="carousel-list carousel-list-first"
            >
              <div class="advertisement-container">
                <h2 class="banner-slogan"></h2>
                <a href="https://www.gogoro.com/smartscooter/viva/mix/">LEARN MORE</a>
              </div>
            </div>
          `,
        },
        {
          html: `
            <div
              class="carousel-list carousel-list-second"
            >
              <video class="gs-video" muted="" playsinline="" autoplay="" loop="" onplay="this.style.opacity = 1;" style="opacity: 1;">
                <source src="//cdn.gogoro.com/resources/pages/landing-page/gs0528/home_vision_1080_v02.mp4" type="video/mp4">
              </video>
              <span class="gs-content-layer">
                <span class="gs-content">
                  <h1 class="gs-title">A Better Way Forward to <span class="d-inline-block">Smarter, Cleaner Cities</span></h1>
                  <span class="gs-desc">Gogoro is reinventing urban transportation with an ecosystem of sustainable energy solutions for the world’s modern cities.</span>
                </span>
              </span>
            </div>
          `,
        },
      ],
    };
  },
};
</script>
<style lang="scss">
.carousel-list {
  height: 100%;
  position: relative;
}
.carousel-list-first {
  background: url(//cdn.gogoro.com/resources/images/landing-page/viva-mix/hb-viva-mix-scooter.png?v1)
      center/contain no-repeat,
    url(//cdn.gogoro.com/resources/images/landing-page/viva-mix/hb-viva-mix-bg.png?v1)
      center/cover no-repeat;

  .advertisement-container {
    position: absolute;
    top: 75%;
    left: 50%;
    transform: translateX(-50%);
    width: 90vw;
    max-width: 402px;

    .banner-slogan {
      height: 70px;
      background-image: url(//cdn.gogoro.com/resources/images/landing-page/viva-mix/hb-viva-mix-slogan-en.svg);
      background-repeat: no-repeat;
      background-size: 100%;
      margin: 0;
    }
    > a {
      display: inline-block;
      border-radius: 32px;
      border: 2px solid #fff;
      padding: 15px 30px;
      color: #fff;
      font-weight: 700;
      text-decoration: none;
      text-transform: uppercase;
      transition: all 0.5s;

      &:hover {
        background-color: #fff;
        color: #5a5a5a;
      }
    }
  }
}
.carousel-list-second {
  video {
    display: block;
    width: 100%;
    height: 100%;
    position: absolute;
    -o-object-fit: cover;
    object-fit: cover;
    left: 0;
    top: 0;
  }
  .gs-content-layer {
    position: absolute;
    width: 100%;
    height: 100%;
    left: 50%;
    top: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #fff;
    max-width: 660px;
    transform: translateX(-50%);

    .gs-title {
      font-size: 54px;
      margin: 0 0 24px 0;
    }
    .gs-desc {
      font-size: 20px;
      line-height: 1.2;
      max-width: 500px;
    }
  }
}
</style>
