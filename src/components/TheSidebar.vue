<template>
  <div class="wrapper">
    <transition name="show">
      <div class="sidebar" v-if="open">
        <a
          href="#"
          class="sidebar-element"
          v-for="item in navElements"
          :key="item"
        >
          Link 1
        </a>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  props: ['open'],
  data: () => {
    return {
      navElements: ['link1', 'link2', 'link3', 'link4', 'link5', 'link6'],
    };
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  position: relative;
}

.sidebar {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;
  width: 100%;
  padding: 15px 20px 0 20px;
  background: #fff;

  .sidebar-element {
    display: block;
    width: 100%;
    margin-bottom: 25px;
    font-family: Roboto;
    font-style: normal;
    font-weight: normal;
    font-size: 25px;
    line-height: 29px;
    color: #000;
    text-align: right;
    text-decoration: none;
    cursor: pointer;
    transition: all .3s ease-in-out;

    &:hover {
      opacity: .2;
    }
  }
}

.show {
  &-enter-from,
  &-leave-to {
    opacity: 0;
    transform: translateX(200px);
  }

  &-enter-active,
  &-leave-active {
    transition: all .5s;
  }
}
</style>
