<template>
  <div>
    demo----->{{money}}
    <button @click="fn">子组件修改父组件</button>
  </div>
</template>

<script>
export default {
  name: 'Demo',
  props: {
    visible: {
      type: Boolean,
      default: false
    },
    money: null
  },
  methods: {
    fn () {
      this.$emit('update:money', 250)
    }
  }
}
</script>

<style>

</style>
