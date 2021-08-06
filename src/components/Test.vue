<template>
  <div class="test">
    <div class="test-left">
      <h2 class="header">Test Title</h2>
      <p class="text">
        It is a long established fact that a reader will be distracted by the
        readable content of a page when looking at its layout. The point of
        using Lorem Ipsum is that it has a more-or-less normal distribution of
        letters,
      </p>
    </div>
    <span
      class="img"
      :class="{ resize: active }"
      @mouseover="mouseOverHandler"
      @mouseleave="mouseOverHandler"
    ></span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      active: false,
    };
  },
  methods: {
    mouseOverHandler() {
      this.active = !this.active;
    },
  },
};
</script>

<style lang="scss" scoped>
.test {
  display: flex;
  justify-content: space-between;
  padding: 20px 40px;
  background: #c4c4c4;
}

.test-left {
  width: 58%;
}

.header {
  margin-bottom: 15px;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  text-transform: uppercase;
}

.text {
  margin-right: 10px;
  font-weight: normal;
  line-height: 12px;
}

.img {
  width: 130px;
  height: 130px;
  background: #ffffff;
  cursor: pointer;
  transition: all .5s ease;

  &.resize {
    width: 150px;
  }
}
</style>
