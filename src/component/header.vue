<template lang="pug">
.header-container 
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
  data() {
    return {
      logoImgSrc: imgLogo,
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
};
</script>
<style lang="scss" scoped>
.header-container {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  transition: all 0.5s;

  &:hover {
    background-color: #000;
  }
  .header-container-inner {
    display: flex;
    max-width: 1140px;
    margin: 0 auto;
    align-items: center;

    > ul {
      list-style-type: none;
      display: flex;
      margin: 0;

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
