<template lang="pug">
Header
.home-container
  Carousel(v-bind:carouselList='carouselList')
  .home-container-body
    .campaign-list
      VerticalCard(v-for="(listItem,listIndex) in campaignList" :key="'carousel-'+listIndex" :verticalCardList="listItem")
    .landing-page-section
      .landing-page-article
        .landing-page-article-slogan
          p(class="font-weight-bold") Gogoro Network
        .landing-page-article-header
          h1 The largest battery swapping network in the world
        .landing-page-article-body
          p Gogoro Network® manages over <b>200,000 battery swaps a day</b> at 2,100 GoStation® across Taiwan, that's enough power to ride 15,000,000 km.
        .landing-page-article-footer
          a(class="font-weight-bold" href="https://network.gogoro.com/tw/en/coverage/") SEE OUR NETWORK <img src="https://cdn.gogoro.com/resources/pages/landing-page/gs0528/icon-aarow.svg?v=2" />
    .media-section
      SimpleIntroduction(v-for="(listItem,listIndex) in introductionList" :key="'simple-introduction-'+listIndex" :introductionData="listItem")
    .eeyo-section
      h1 Introducing Gogoro Eeyo
      p From the cloud to the road, this is eBike reimagined. <br />Ultralight, totally digital, and an absolute blast to ride.
      a(class="font-weight-bold" href="https://eeyo.bike/tw/") LEARN MORE <img src="https://cdn.gogoro.com/resources/pages/landing-page/gs0528/icon-aarow.svg?v=2" />
      img(src="https://cdn.gogoro.com/resources/pages/landing-page/gs0528/05_Profileshot_Right_Side.png")
    .quotes-section
      .quotes-section-article(:class="quotesData.animation")
        a(href="quotesData.list[quotesData.activeIndex].href") 
          blockquote
            q {{quotesData.list[quotesData.activeIndex].quote}}
            p - {{quotesData.list[quotesData.activeIndex].note}}
      ul.quotes-tabs
        li(v-for="(listItem,listIndex) in quotesData.list" :key="'quotes-tabs-'+listIndex" :class="{active:(listIndex===quotesData.activeIndex)}" @click="quotesTabsHandle(listIndex)") 
          span(v-if="listItem.tabText") {{listItem.tabText}}
          img(v-else-if="listItem.tabImgSrc" :src="listItem.tabImgSrc")
</template>

<script>
import Header from "../component/header";
import Carousel from "../component/carousel";
import VerticalCard from "../component/vertical-card";
import SimpleIntroduction from "../component/simple-introduction";

export default {
  name: "Home",
  components: { Header, Carousel, VerticalCard, SimpleIntroduction },
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
              <a href="https://www.gogoro.com/about/">
                <video class="gs-video" muted="" playsinline="" autoplay="" loop="" onplay="this.style.opacity = 1;" style="opacity: 1;">
                  <source src="//cdn.gogoro.com/resources/pages/landing-page/gs0528/home_vision_1080_v02.mp4" type="video/mp4">
                </video>
                <span class="gs-content-layer">
                  <span class="gs-content">
                    <h1 class="gs-title">A Better Way Forward to <span class="d-inline-block">Smarter, Cleaner Cities</span></h1>
                    <span class="gs-desc">Gogoro is reinventing urban transportation with an ecosystem of sustainable energy solutions for the world’s modern cities.</span>
                  </span>
                </span>
              </a>
            </div>
          `,
        },
      ],
      campaignList: [
        {
          target: "_self",
          href: "http://www.gogoro.com/gogoro-network/",
          bgImgSrc:
            "https://www.gogoro.com/uploads/landing_pages/2-campaign1-background-e3b88377e474f0386c7bfbc9f442227c73d79865.png?1590659699",
          title: "Smarter Energy",
          description: "Battery swapping is cleaner, faster & easier",
        },
        {
          target: "_self",
          href: "http://www.gogoro.com/gogoro-network/",
          bgImgSrc:
            "https://www.gogoro.com/uploads/landing_pages/2-campaign2-background-a4b8ef537d3b88a684eee733d9886a9634c9564a.png?1590570315",
          title: "Smarter Rides",
          description: "Experience a ride like no other",
        },
        {
          target: "_self",
          href: "http://www.gogoro.com/gogoro-network/",
          bgImgSrc:
            "https://www.gogoro.com/uploads/landing_pages/2-campaign3-background-e608d89f7f5e1dd4ca01da871c9f2d18fa4ceb3b.png?1590570315",
          title: "Smarter Sharing",
          description: "Ride when you like, swap as you go",
        },
      ],
      introductionList: [
        {
          title: "5 Partners and Growing",
          text: "",
          isHTML: true,
          html: "Powered by <br />Gogoro Network",
          href: "https://network.gogoro.com/tw/en/scooter/",
          target: "_self",
          style: {
            height: "340px",
            backgroundImage:
              "url('https://www.gogoro.com/uploads/landing_pages/2-blog-post1-background-cd09a35997763fe78b226f247857bef12f02d0a6.png?1590570315')",
          },
        },
        {
          title: "Blog",
          text: "",
          isHTML: true,
          html: "Hero & Gogoro <br />heads to India",
          href:
            "https://www.gogoro.com/news/Gogoro-Battery-Swapping-India-Hero/",
          target: "_self",
          style: {
            height: "340px",
            backgroundImage:
              "url('https://www.gogoro.com/uploads/landing_pages/2-social-post-background-56588be5a509ae7d8125699fa4a6a5757930e33a.jpg?1619595003')",
          },
        },
      ],
      quotesData: {
        animation: "animation-fadein",
        activeIndex: 0,
        list: [
          {
            quote: "You have to see it to really appreciate how cool it is,",
            note: "Al Gore, Wired, December 2017",
            href:
              "https://www.wired.co.uk/article/al-gore-generation-sustainable-capitalism",
            tabText: "",
            tabImgSrc:
              "https://cdn.gogoro.com/resources/images/landing-page/quotes_logo_wired_on.jpg",
          },
          {
            quote: "The 9 Coolest Gadgets from CES 2016",
            note: "Time",
            href: "https://time.com/4169302/ces-2016-coolest/",
            tabText: "",
            tabImgSrc:
              "https://cdn.gogoro.com/resources/images/landing-page/quotes_logo_time_on.jpg",
          },
          {
            quote: "2018 Asian Company of the Year",
            note: "Cleantech 100",
            href:
              "https://www.cleantech.com/release/cleantech-group-unveils-the-2018-global-cleantech-100-list/",
            tabText: "",
            tabImgSrc:
              "https://cdn.gogoro.com/resources/images/landing-page/quotes_logo_cleantech_on.jpg",
          },
          {
            quote: "2015 CES Best In Show Award",
            note: "The Verge",
            href:
              "https://www.theverge.com/2015/1/9/7509787/verge-awards-best-of-ces-2015",
            tabText: "",
            tabImgSrc:
              "https://cdn.gogoro.com/resources/images/landing-page/quotes_logo_verge_on.jpg",
          },
          {
            quote: "2017 Nikkei Asian Review Award for Excellence",
            note: "Nikkei Asian Review",
            href:
              "https://asia.nikkei.com/magazine/20180111/Business/Gogoro-wins-the-Nikkei-Asian-Review-Award-for-Excellence",
            tabText: "",
            tabImgSrc:
              "https://cdn.gogoro.com/resources/images/landing-page/quotes_logo_nikkei_on.jpg",
          },
          {
            quote: "Selected for the 2016 Sustainia 1000",
            note: "Sustainia",
            href:
              "https://blog.gogoro.com/en/gogoro-selected-for-the-2016-sustainia100e",
            tabText: "",
            tabImgSrc:
              "https://cdn.gogoro.com/resources/images/landing-page/quotes_logo_sustania_on.jpg",
          },
        ],
      },
    };
  },
  methods: {
    quotesTabsHandle(activeIndex) {
      this.quotesData.animation = "animation-fadeout";
      setTimeout(() => {
        this.quotesData.activeIndex = activeIndex;
        this.quotesData.animation = "animation-fadein";
      }, 700);
    },
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
.home-container-body {
  width: 100%;
  margin: 10px auto;
  max-width: 1280px;

  .campaign-list {
    display: flex;
    justify-content: space-between;

    .vertical-card-container {
      width: calc(100% / 3 - 8px);
    }
  }
  .landing-page-section {
    display: flex;
    align-items: center;
    background-image: linear-gradient(60deg, #40fdcb, #40fdcb 7%, #24ee2c);
    position: relative;
    height: 650px;
    margin-top: 10px;

    &:before {
      content: "";
      display: block;
      width: 100%;
      background-image: url("https://cdn.gogoro.com/resources/images/landing-page/station-gn@2x.png?v2");
      position: absolute;
      right: 0;
      top: 0;
      height: 100%;
      background-size: contain;
      background-position: 90% 0;
      background-repeat: no-repeat;
    }

    .landing-page-article {
      max-width: 378px;
      text-align: left;
      position: relative;
      z-index: 1;
      left: 100px;

      .landing-page-article-slogan {
        opacity: 0.7;
        margin: 0 0 46px 0;
      }
      .landing-page-article-header {
        color: #000;
        margin: 0 0 20px 0;
      }
      .landing-page-article-body {
        margin: 0 0 32px 0;
      }
      .landing-page-article-footer {
        > a {
          display: flex;
          align-items: center;
        }
      }
    }
  }
  .media-section {
    display: flex;
    justify-content: space-between;
    margin-top: 10px;

    .simple-introduction-container {
      width: calc(100% / 2 - 5px);
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    }
  }
  .eeyo-section {
    padding: 60px 0 0 0;
    height: 620px;
    overflow: hidden;
    position: relative;
    background-color: #f2f2f2;
    margin-top: 10px;

    > h1 {
      font-size: 42px;
      margin: 0 0 20px 0;
    }
    > p {
      max-width: 464px;
      margin: 0 auto;
    }
    > a {
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 36px 0 40px 0;
    }
    > img {
      width: 100%;
      max-width: 900px;
      position: absolute;
      bottom: -130px;
      left: 50%;
      transform: translateX(-50%);
    }
  }
  .quotes-section {
    .quotes-section-article {
      background-color: #fff;
      margin-top: 10px;
      padding: var(--spacing-xxl-6) 0 var(--spacing-xxl-2);

      q {
        font-size: 36px;
        color: #323237;
      }
      p {
        color: #b9bcbf;
      }
    }
    .quotes-tabs {
      background-color: #e6e6e6;
      display: flex;
      justify-content: center;

      > li {
        position: relative;
        cursor: pointer;
        padding: 0 var(--spacing-m);
        opacity: 0.3;

        &.active {
          opacity: 1;

          &::before {
            content: "";
            display: block;
            position: absolute;
            left: 50%;
            top: 0;
            margin-left: -10px;
            border-width: 15px 10px;
            border-color: #fff transparent transparent transparent;
            border-style: solid;
          }
        }
        > span {
          padding: 25px 0 15px;
        }
      }
    }
  }
}
</style>
