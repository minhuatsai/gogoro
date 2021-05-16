<template lang="pug">
.header-container(:style="{backgroundColor:`rgba(0, 0, 0,${headerBackgroundOpacity})`}") 
    .header-container-inner
        router-link(to="/")
            img.img-logo(:src='logoImgSrc') 
        ul 
            li(v-for='list in headerList' :key='list.text') 
                a(v-if='list.link.type === \'absolute\'' :href='list.link.href') {{ list.text }} 
                router-link(v-else-if='list.link.type=== \'relative\'' :to='list.link.href') {{ list.text }}
</template>
<script>
import imgLogo from "../assets/img/logo.svg";
export default {
  name: "Header",
  components: {},
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  data() {
    return {
      logoImgSrc: imgLogo,
      headerBackgroundOpacity: 0,
      headerList: [
        {
          text: "Smartscooter®",
          link: {
            type: "absolute",
            href: "https://www.gogoro.com/smartscooter/",
          },
        },
        {
          text: "Gogoro Network®",
          link: {
            type: "absolute",
            href: "https://www.gogoro.com/gogoro-network/",
          },
        },
        {
          text: "News",
          link: {
            type: "absolute",
            href: "https://www.gogoro.com/news/",
          },
        },
      ],
    };
  },
  methods: {
    handleScroll() {
      if (window.scrollY >= 300) {
        this.headerBackgroundOpacity = 1;
      } else {
        this.headerBackgroundOpacity = window.scrollY / 300;
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.header-container {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  transition: all 0.5s;
  display: flex;
  justify-content: center;
  z-index: 444444;

  &:hover {
    background-color: rgba(0, 0, 0, 1) !important;
  }
  .header-container-inner {
    display: flex;
    align-items: center;
    width: 85%;

    > ul {
      list-style-type: none;
      display: flex;
      margin: 0 0 0 30px;

      li {
        cursor: pointer;

        &:hover {
          a {
            color: #00d7ff;
          }
        }
        a {
          color: #fff;
          padding: 0 var(--spacing-m);
          display: flex;
          align-items: center;
          height: 60px;
        }
      }
    }
  }
}
</style>
<style lang="scss">
html {
  background-color: #d7d7d7;
}
</style>
