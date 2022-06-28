<template>
  <div class="my-tab-bar">
    <div
      :class="['tab-item', { current: currentIndex === index }]"
      v-for="(item, index) in tabList"
      :key="index"
      @click="changeName(index, item.componentName)"
    >
      <!-- 图标 -->
      <span :class="`iconfont ${item.iconText}`"></span>
      <!-- 文字 -->
      <span>{{ item.text }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tabList: {
      type: Array,
      required: true,
      validator(data) {
        const len = data.length
        if (len > 2 && len < 5) {
          return true
        } else {
          throw new Error('数组长度必须在2-5之间')
        }
      }
    }
  },
  data() {
    return {
      currentIndex: 0
    }
  },
  methods: {
    changeName(index, compName) {
      this.currentIndex = index
      this.$emit('change-component', compName)
    }
  }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;
  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.current {
  color: green;
  .iconfont {
    color: greenyellow;
  }
}
</style>
