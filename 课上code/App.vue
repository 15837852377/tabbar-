<template>
  <div>
    <input type="text" v-focus="msg" />
    <button @click="msg = '你好世界'">更新msg</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: 'hello,world'
    }
  },
  directives: {
    focus: {
      inserted(el, { value }) {
        el.focus()
        el.value = value
      },
      update(el, binding) {
        el.focus()
        el.value = binding.value
      }
    }
  }
}
</script>

<style></style>
