<template>
  <div>
    <h1>动态组件</h1>
    <button @click="componentName = 'MyAccount'">显示Accout组件</button>
    <button @click="componentName = 'MyIfo'">显示MyIfo</button>
    <hr />
    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>
  </div>
</template>

<script>
// 动态组件
// 1.方式一 通过v-if去控制
// 2.component 内置的组件
// 3.必须通过is属性指定显示组件的名字
// 4.is属性的
import MyAccount from '@/components/MyAccount'
import MyIfo from '@/components/MyInfo'

export default {
  components: {
    MyAccount,
    MyIfo
  },
  data() {
    return {
      isShowAccount: true,
      componentName: 'MyAccount'
    }
  }
}
</script>

<style></style>
