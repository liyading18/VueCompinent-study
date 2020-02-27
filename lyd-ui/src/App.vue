<template>
  <div id="app">
    自己封装组件
    <!-- <lyd-input
      placeholder="请输入姓名"
      type="password"
      name="username"
      disabled
    ></lyd-input>
    <lyd-input v-model="value"></lyd-input> -->
    <lyd-input v-model="value" clearable></lyd-input>
    <lyd-input v-model="value" type="password" show-password></lyd-input>
  </div>
</template>

<script>
export default {
  data () {
    return {
      value: '李亚鼎'
    }
  }
}
</script>

<style lang="scss">
  #app {
    .lyd-input {
      width: 180px;
    }
  }
</style>
