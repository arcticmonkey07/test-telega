<template>
  <div class="content">
    <div class="container">
      <h1 class="header">Heading</h1>
      <Article right="right" />
      <Article left="left" />
      <transition
        name="expand"
        @enter="enter"
        @after-enter="afterEnter"
        @leave="leave"
      >
        <div v-show="isOpen">
          <Article right="right" />
          <Article left="left" />
        </div>
      </transition>
      <button class="btn-more" @click="articleHandler">{{ btnText }}</button>
    </div>
  </div>
</template>

<script>
import Article from '@/components/Article.vue';

export default {
  components: {
    Article,
  },
  data: () => {
    return {
      isOpen: false,
    };
  },
  methods: {
    articleHandler() {
      this.isOpen = !this.isOpen;
    },
    enter(el) {
      el.style.height = 'auto';
      const height = getComputedStyle(el).height;
      el.style.height = 0;
      getComputedStyle(el);
      setTimeout(() => {
        el.style.height = height;
      });
    },
    afterEnter(el) {
      el.style.height = 'auto';
    },
    leave(el) {
      el.style.height = getComputedStyle(el).height;
      getComputedStyle(el);
      setTimeout(() => {
        el.style.height = 0;
      });
    },
  },
  computed: {
    btnText: function() {
      if (this.isOpen) {
        return "Hide"
      }
      return "Show More"
    }
  }
};
</script>

<style lang="scss" scoped>

.btn-more {
  display: block;
  margin: 0 auto;
  padding: 15px 41px;
  font-weight: normal;
  font-size: 10px;
  line-height: 12px;
  color: #000000;
  text-transform: uppercase;
  background: #ffffff;
  border: 2px solid #f4f4f4;
  border-radius: 15px;
  box-sizing: border-box;
  cursor: pointer;
  transition: all .3s ease-in-out;

  &:hover {
    color: #c3c3c3;
    opacity: 0.5;
  }
}

.expand-enter-active,
.expand-leave-active {
  transition: height 0.5s ease-in-out;
  overflow: hidden;
}
</style>
