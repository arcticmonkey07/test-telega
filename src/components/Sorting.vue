<template>
  <div class="content">
    <div class="container">
      <h2 class="header">Sorting</h2>
      <div class="input-block">
        <input
          type="text"
          class="input"
          v-model="query"
          placeholder="Enter title name"
          @keyup="computedBlocks"
        />
        <button class="cross" @click="clear">X</button>
      </div>
      <transition-group class="blocks" name="sort" tag="ul">
        <li class="block" v-for="block in blocks" :key="block">
          <span class="block-num">{{ block }}</span>
        </li>
      </transition-group>
    </div>
  </div>
</template>

<script>
import _ from "lodash";

export default {

  data() {
    return {
      query: '',
      blocks: [2, 6, 4, 1, 5, 3],
      sortedArray: []
    };
  },
  methods: {
    computedBlocks() {
      this.sortedArray = this.blocks;
      return this.sortedArray.sort(function(a, b) {
        return a - b;
      });
    },
    clear() {
      this.query = '';
      return this.blocks = _.shuffle(this.blocks);
    }
  },
};
</script>

<style lang="scss" scoped>
.input-block {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 15px;
}

.input {
  width: 88.1%;
  height: 30px;
  padding: 9px;
  font-weight: normal;
  font-size: 10px;
  line-height: 12px;
  background: #ffffff;
  border: 2px solid #f4f4f4;
  box-sizing: border-box;
  border-radius: 5px;
  transition: all .3s ease-in-out;

  &::-webkit-input-placeholder {
    font-size: 10px;
    line-height: 12px;
    color: #000;
  }

  &::-moz-placeholder {
    font-size: 10px;
    line-height: 12px;
    color: #000;
  }

  &::-ms-input-placeholder {
    font-size: 10px;
    line-height: 12px;
    color: #000;
  }

  &:hover {
    opacity: 0.5;
  }
}

.cross {
  width: 30px;
  height: 30px;
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
  background: #ffffff;
  border: 2px solid #f4f4f4;
  box-sizing: border-box;
  border-radius: 5px;
  cursor: pointer;
  transition: all .3s ease-in-out;

  &:hover {
    opacity: 0.5;
  }
}

.blocks {
  display: flex;
  flex-wrap: wrap;
  margin: 0;
  padding: 0;
  list-style: none;
}

.block {
  display: flex;
  align-items: flex-end;
  width: 100px;
  height: 125px;
  margin: 0 9px 10px 0;
  padding: 15px;
  background: #c4c4c4;

  &:nth-child(3n + 3) {
    margin-right: 0;
  }
}

.block-num {
  font-weight: bold;
  font-size: 14px;
  line-height: 16px;
}

.sort-move {
  transition: transform 0.5s ease-out;
}
</style>
