<template>
  <div class="topbar">
    <span class="logo-img" alt="logo"></span>
    <a href="#" class="logo">Logo</a>
    <button
      class="burger"
      :class="{ open: isOpen }"
      @click="
        $emit('togglenav');
        burgerTransform();
      "
    >
      <span class="burger-line"></span>
    </button>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      isOpen: false,
    };
  },
  methods: {
    burgerTransform() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style lang="scss" scoped>
.topbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 45px;
  padding: 10px 20px;
  border-bottom: 1px solid #c4c4c4;
  color: #000;
}

.logo-img {
  display: block;
  width: 25px;
  height: 25px;
  margin-right: 10px;
  background-color: #c4c4c4;
}

.logo {
  display: block;
  font-family: Roboto, sans-serif;
  font-style: normal;
  font-weight: bold;
  font-size: 11px;
  line-height: 13px;
  text-decoration: none;
}

.burger {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 25px;
  margin-left: auto;
  color: #000;
  border: none;
  background-color: transparent;
  text-decoration: none;
  cursor: pointer;
  transition: all .3s ease-in-out;

  &:hover {
      opacity: .5;
    }
}

.burger-line {
  display: block;
  position: relative;
  width: 25px;
  height: 3px;
  background: #c4c4c4;
  transition: all 0.5s ease-in-out;

  &:before,
  &:after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 25px;
    height: 3px;
    background: #c4c4c4;
    transition: all 0.5s ease-in-out;
  }

  &:before {
    transform: translateY(-7px);
  }

  &:after {
    transform: translateY(7px);
  }
}

.burger.open .burger-line {
  transform: translateX(-10px);
  background: transparent;
}

.burger.open .burger-line:before {
  transform: rotate(45deg) translate(7px, -7px);
}

.burger.open .burger-line:after {
  transform: rotate(-45deg) translate(7px, 7px);
}

</style>
