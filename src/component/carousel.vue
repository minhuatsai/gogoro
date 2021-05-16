<template lang="pug">
.carousel-container
  ul(:class="carouselData.className")
    li(v-for="(listItem,listIndex) in carouselData.list" :key="'carousel-'+listIndex" v-html="listItem.html" class="carousel-list-container" :class="{active:listItem.active}")
  .slick-dot
    span(v-for="(listItem,listIndex) in carouselData.list" :key="'slick-dot-'+listIndex" :class="{active:listItem.active}" @click="carouselChange(listIndex);" ref="slickActiveItem")
</template>
<script>
export default {
  name: "carousel",
  props: ["carouselData"],
  mounted() {
    this.stopCarousel = setInterval(() => {
      this.activeIndex++;
      if (this.activeIndex === this.$props.carouselData.list.length) {
        this.activeIndex = 0;
      }
      this.$props.carouselData.list.forEach((listItem, listIndex) => {
        listItem.active = this.activeIndex === listIndex ? true : false;
      });
    }, this.duration);
  },
  data() {
    return {
      activeIndex: 0,
      duration: 3000,
      stopCarousel: null,
      listRefs: [],
    };
  },
  methods: {
    carouselChange(activeIndex) {
      this.activeIndex = activeIndex;
      this.$props.carouselData.list.forEach((listItem, listIndex) => {
        listItem.active = activeIndex === listIndex ? true : false;
      });
      clearInterval(this.stopCarousel);

      this.$emit("carousel-change", activeIndex);
    },
  },
};
</script>
<style lang="scss" scoped>
.carousel-container {
  min-height: 300px;
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
    display: none;
    height: 100%;

    &.active {
      display: block;
    }
  }
}
</style>
