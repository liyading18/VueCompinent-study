<template>
  <label class="lyd-switch" :class="{'is-checked': value}" @click="handleClick">
    <span class="lyd-switch_core">
      <span class="lyd-switch_button"></span>
    </span>
  </label>
</template>

<script>
export default {
  name: 'LydSwitch',
  props: {
    value: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleClick () {
      this.$emit('input', !this.value)
    }
  }
}
</script>

<style lang="scss">
  .lyd-switch {
    display: inline-flex;
    align-items: center;
    position: relative;
    font-size: 14px;
    line-height: 20px;
    height: 20px;
    vertical-align: middle;
    .lyd-switch_core {
      margin: 0;
      display: inline-block;
      position: relative;
      width: 40px;
      height: 20px;
      border: 1px solid #dcdfe6;
      outline: none;
      border-radius: 10px;
      box-sizing: border-box;
      background: #dcdfe6;
      cursor: pointer;
      transition: border-color .3s,background-color .3s;
      vertical-align: middle;
      .lyd-switch_button {
        position: absolute;
        top: 1px;
        left: 1px;
        border-radius: 100%;
        transition: all .3s;
        width: 16px;
        height: 16px;
        background-color: #fff;
      }
    }
  }
  .lyd-switch.is-checked {
    .lyd-switch_core {
      border-color: #409eff;
      background-color: #409eff;
      .lyd-switch_button {
        transform: translateX(20px);
      }
    }
  }
</style>
