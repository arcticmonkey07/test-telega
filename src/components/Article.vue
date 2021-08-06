<template>
  <article class="article" v-if="isRight">
    <p class="text">
      It is a long established fact that a reader will be distracted by the
      readable content of a page when looking at its layout. The point of using
      Lorem Ipsum is that it has a more-or-less normal distribution of letters,
    </p>
    <span class="img"></span>
  </article>
  <article class="article" v-if="isLeft">
    <span class="img"></span>
    <p class="text">
      It is a long established fact that a reader will be distracted by the
      readable content of a page when looking at its layout. The point of using
      Lorem Ipsum is that it has a more-or-less normal distribution of letters,
    </p>
  </article>
</template>

<script>
export default {
  props: ['right', 'left'],
  data() {
    return {
      isRight: this.right,
      isLeft: this.left
    };
  },
};
</script>

<style lang="scss" scoped>
.article {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;

  .text {
    width: 62%;
    line-height: 12px;
  }

  .img {
    width: 100px;
    height: 100px;
    background: #c4c4c4;
  }
}
</style>
