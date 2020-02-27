<template>
  <div id="app">
    自己封装组件
    <!-- <lyd-button type="primary">插槽slot-登陆</lyd-button>
    <lyd-button type="success">插槽slot-取消</lyd-button>
    <lyd-button plain>button父传子plain属性</lyd-button>
    <lyd-button icon="icon-meinv" @click="fn">button父传子icon字体图标</lyd-button>
    <lyd-button icon="icon-meinv" @click="fn" disabled>button的disabled属性</lyd-button> -->
    <!-- <lyd-dialog title="温馨提示"></lyd-dialog> -->
    <!-- <lyd-dialog>
      <template v-slot:title>
        <h3>v-slot插槽标题</h3>
      </template>
    </lyd-dialog> -->
    <lyd-button type="primary" @click="visible=true">点击按钮</lyd-button>
    <!-- <lyd-dialog title="温馨提示" width="20%" top="50px" :visible="visible" @close="close"> -->
    <lyd-dialog title="温馨提示" width="20%" top="50px" :visible.sync="visible">
      <ul>
        <li>传递给子组件的默认插槽slot</li>
        <li>1</li>
        <li>2</li>
      </ul>
      <template v-slot:footer>
        <lyd-button @click="visible=false">取消</lyd-button>
        <lyd-button type="primary" @click="visible=false">确定</lyd-button>
      </template>
    </lyd-dialog>
    <!-- <transition>
      <div v-show="visible">测试Vue自带的动画显示与隐藏</div>
    </transition> -->
  </div>
</template>

<script>
export default {
  data () {
    return {
      visible: false
    }
  },
  methods: {
    fn () {
      console.log('父组件的点击函数')
    },
    close (value) {
      this.visible = value
    }
  }
}
</script>

<style lang="scss">
  .v-enter-active {
    animation: run .5s;
  }
  .v-leave-active {
    animation: run .5s reverse;
  }
  @keyframes run {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
</style>
