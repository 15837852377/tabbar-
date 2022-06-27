<template>
  <div>
    <input type="text" v-focus="msg" />
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
      }
    }
  }
}
</script>

<style></style>
