<template lang="pug">
.carousel-container
  ul
    li(v-for="(listItem,listIndex) in carouselList" :key="'carousel-'+listIndex" v-html="listItem.html" class="carousel-list-container" :class="{active:listItem.active}")
  .slick-dot
    span(v-for="(listItem,listIndex) in carouselList" :key="'slick-dot-'+listIndex" :class="{active:listItem.active}" @click="listActiveHandle(listIndex)")
</template>
<script>
export default {
  name: "carousel",
  props: ["carouselList"],
  methods: {
    listActiveHandle(activeIndex) {
      this.$props.carouselList.forEach((listItem, listIndex) => {
        listItem.active = activeIndex === listIndex ? true : false;
      });
    },
  },
};
</script>
<style lang="scss" scoped>
.carousel-container {
  position: relative;

  .slick-dot {
    position: absolute;
    width: 100%;
    height: 20px;
    display: flex;
    justify-content: center;
    bottom: 10px;

    > span {
      width: 10px;
      height: 10px;
      background-color: #737d82;
      border-radius: 50%;
      cursor: pointer;
      margin: 0px 10px;
      border: 2px solid transparent;

      &.active {
        border: 2px solid #fff;
        background-color: rgba(115, 125, 130, 0);
      }
    }
  }
  .carousel-list-container {
    height: 85vh;
    display: none;

    &.active {
      display: block;
    }
  }
}
</style>
