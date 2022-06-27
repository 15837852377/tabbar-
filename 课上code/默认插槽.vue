<template>
  <div id="app">
    <MyPannel />
    <my-pannel title="静夜思">
      <p>床前明月光,</p>
      <p>疑是地上霜</p>
      <p>举头望明月，</p>
      <p>低头思故乡。</p>
    </my-pannel>
  </div>
</template>

<script>
import MyPannel from '@/components/MyPannel'
export default {
  components: {
    [MyPannel.name]: MyPannel
  }
}
</script>

<style></style>
