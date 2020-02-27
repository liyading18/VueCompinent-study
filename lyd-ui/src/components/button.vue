<template>
  <button class="lyd-button" :class="[`lyd-button--${type}`, {
    'is-plain': plain
  }]"
  @click="handleClick"
  :disabled="disabled"
  >
    <i :class="icon"></i>
    <span v-if="$slots.default">
      <slot></slot>
    </span>
  </button>
</template>

<script>
export default {
  name: 'LydButton',
  props: {
    type: {
      type: String,
      default: 'default'
    },
    plain: {
      type: Boolean,
      default: false
    },
    icon: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleClick (e) {
      this.$emit('click', e)
    }
  }
}
</script>

<style lang="scss" scoped>
  .lyd-button {
    display: inline-block;
    line-height: 1;
    white-space: nowrap;
    cursor: pointer;
    background: #ffffff;
    border: 1px solid #dcdfe6;
    color: #606266;
    text-align: center;
    box-sizing: border-box;
    outline: none;
    margin: 10px;
    transition: 0.1s;
    font-weight: 500;
    &:hover{
        color:aqua;
    }
  }
  .lyd-button--primary {
    background-color: #f00;
  }
  .lyd-button--success {
    background-color: #fadd;
  }
  .is-plain {
    border: solid 1px black;
    border-radius: 50%;
  }
</style>
