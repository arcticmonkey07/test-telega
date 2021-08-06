<template>
  <div id="app" class="app">
    <TheTopbar @togglenav="navOpen = !navOpen" />
    <TheSidebar :open="navOpen" />
    <Content />
    <Test />
    <Sorting />
  </div>
</template>

<script>
import TheTopbar from '@/components/TheTopbar';
import TheSidebar from '@/components/TheSidebar';
import Content from '@/components/Content';
import Test from '@/components/Test';
import Sorting from '@/components/Sorting';

export default {
  name: 'App',
  data: () => {
    return {
      navOpen: false,
    };
  },
  components: {
    TheTopbar,
    TheSidebar,
    Content,
    Test,
    Sorting
  },
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  font-size: 10px;
  font-family: 'Roboto', sans-serif;
  color: #000000;
}

.app {
  width: 400px;
  min-height: 100vh;
  margin: 0 auto;
  border: 1px solid #c4c4c4;
}

.content {
  padding: 20px;
  background: #e5e5e5;
}

.container {
  margin: 0 auto;
  padding: 20px;
  background: #fff;
  border-radius: 15px;
  transition: all 0.3s ease-in-out;
}

.header {
  margin: 0 0 20px 0;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  color: #000000;
  text-align: center;
  text-transform: uppercase;
}
</style>
