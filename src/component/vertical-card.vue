<template lang="pug">
.vertical-card-container
    a(href='http://www.gogoro.com/gogoro-network/' :target='verticalCardList.title' :style='style')
        .vertical-card-header
            h2.campaign-title {{verticalCardList.title}}
            p {{verticalCardList.description}}
</template>
<script>
export default {
  name: "vertical-card",
  props: ["verticalCardList"],
  data() {
    return {
      style: {
        "background-image": `url(${this.$props.verticalCardList.bgImgSrc})`,
      },
    };
  },
};
</script>
<style lang="scss" scoped>
.vertical-card-container {
  a {
    height: 510px;
    display: block;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    padding-top: var(--spacing-xxl-6);
  }
}
</style>
