<template>
  <transition name="dialog-fade">
    <div class="lyd-dialog-wrapper" v-show="visible"  @click.self="handleClose">
      <div class="lyd-dialog" :style="{width, marginTop: top}">
        <div class="lyd-dialog_header">
          <slot name="title">
            <span class="lyd-dialog_title">{{ title }}</span>
          </slot>
          <button class="lyd-dialog_headerbtn" @click="handleClose">
            <i class="icon-meinv"></i>
          </button>
        </div>
        <div class="lyd-dialog_body">
          <!-- <span>这是一段信息</span> -->
          <slot></slot>
        </div>
        <div class="lyd-dialog_footer" v-if="$slots.footer">
          <!-- <lyd-button>取消</lyd-button>
          <lyd-button type="primary">确定</lyd-button> -->
          <slot name="footer"></slot>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import './button'
export default {
  name: 'LydDialog',
  props: {
    title: {
      type: String,
      default: '提示'
    },
    width: {
      type: String,
      default: '50%'
    },
    top: {
      type: String,
      default: '200px'
    },
    visible: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleClose () {
      console.log('子组件的点击事件')
      // this.$emit('close', false)`
      this.$emit('update:visible', false)
    }
  }
}
</script>

<style lang="scss" scoped>
  .dialog-fade-enter-active {
    animation: run .5s;
  }
  .dialog-fade-leave-active {
    animation: run .5s reverse;
  }
  @keyframes run {
    0% {
      opacity: 0;
      transform: translateY(-20px)
    }
    100% {
      opacity: 1;
      transform: translateY(0px);
    }
  }
  .lyd-dialog-wrapper {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    overflow: auto;
    margin: 0;
    z-index: 2001;
    background-color: rgba(0, 0, 0, .5);
    .lyd-dialog {
      position: relative;
      margin: 15vh auto 50px;
      background-color: #ffffff;
      border-radius: 2px;
      box-shadow: 0 1px 3px rgba(0, 0, 0, .3);
      box-sizing: border-box;
      width: 30%;
      &_header {
        padding: 20px 20px 10px;
        .lyd-dialog_title {
          line-height: 24px;
          font-size: 18px;
          color: #303133;
        }
        .lyd-dialog_headerbtn {
          position: absolute;
          top: 20px;
          right: 20px;
          padding: 0;
          background: transparent;
          border: none;
          outline: none;
          cursor: pointer;
          font-size: 16px;
          .icon-meinv {
            color: #909399;
          }
        }
      }
      &_body {
        padding: 30px 20px;
        color: #606266;
        font-size: 14px;
        word-break: break-all;
      }
      &_footer {
        padding: 10px 20px 20px;
        text-align: right;
        box-sizing: border-box;
      }
    }
  }
</style>
