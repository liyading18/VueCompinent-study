<template>
  <div class="lyd-input lyd-input--suffix">
    <input
      class="lyd-input_inner"
      :class="{'is-disabled': disabled}"
      :placeholder="placeholder"
      :type="type"
      :disabled="disabled"
      :value="value"
      @input="handleInput"
    >
    <span class="lyd-input_suffix">
      <i class="icon-meinv" v-if="clearable"></i>
      <i class="icon-meinvguanjia" v-if="showPassword"></i>
    </span>
  </div>
</template>

<script>
export default {
  name: 'lyd-input',
  props: {
    clearable: {
      type: Boolean,
      default: false
    },
    showPassword: {
      type: Boolean,
      default: false
    },
    value: {
      type: String,
      default: ''
    },
    disabled: {
      type: Boolean,
      default: false
    },
    name: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: 'text'
    },
    placeholder: {
      type: String,
      default: ''
    }
  },
  methods: {
    handleInput (e) {
      this.$emit('input', e.target.value)
    }
  }
}
</script>

<style lang="scss">
  .lyd-input {
    width: 100%;
    position: relative;
    font-size: 14px;
    display: inline-block;
    .lyd-input_inner {
      -webkit-appearance: none;
      background-color: #ffffff;
      background-image: none;
      border-radius: 4px;
      border: 1px solid #dcdfe6;
      box-sizing: border-box;
      color: #606266;
      display: inline-block;
      font-size: inherit;
      height: 40px;
      line-height: 40px;
      outline: none;
      padding: 0 15px;
      transition: border-color .2s cubic-bezier(.645, .045, .355, 1);
      width: 100%;
      &:focus {
        outline: none;
        border-color: #409eff;
      }
      &.is-disabled {
       background-color: #f5f7fa;
       border-color: #e4e7ed;
       color: #c0c4cc;
       cursor: not-allowed;
      }
    }
  }
  .lyd-input--suffix {
    .lyd-input_inner {
      padding-right: 30px;
    }
    .lyd-input_suffix {
      position: absolute;
      height: 100%;
      right: 10px;
      top: 0;
      line-height: 40px;
      text-align: center;
      color: #3c0ccc;
      transition: all .3s;
      z-index: 900;
      i {
        color: #c0c4cc;
        font-size: 14px;
        cursor: pointer;
        transition: color .2s cubic-bezier(.645,.045,.355,1);
      }
    }
  }
</style>
