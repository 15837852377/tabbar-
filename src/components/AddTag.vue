<template>
  <div>
    <button
      class="btn btn-primary btn-sm"
      v-if="isShowBtn"
      @click="isShowBtn = false"
    >
      +Tag
    </button>
    <input
      v-else
      v-focus
      v-model="tagName"
      type="text"
      style="width: 70px"
      @blur="addTag"
      @keydown.enter="addTag"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShowBtn: true,
      tagName: ''
    }
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus()
      }
    }
  },
  methods: {
    addTag() {
      this.isShowBtn = true
      if (this.tagName.trim() !== '') {
        this.$emit('add-tag', this.tagName)
      }
      this.tagName = ''
    }
  }
}
</script>

<style></style>
