<template>
  <div id="app">
    <!-- <com-setup p1="aaaaaaa" /> -->
    <!-- <com-ref /> -->
    <!-- <com-torefs /> -->
    <!-- <com-computed /> -->
    <!-- <com-watch1 /> -->
    <!-- <com-watch2 /> -->
    <!-- <com-watch3 /> -->

    <h1>父组件</h1>
    <button @click="showCom">打印 comRef 的值</button>
    <br />
    <!-- 点击 App.vue 中的按钮，切换子组件中文字的颜色 -->
    <button @click="themeColor='red'">红色</button>
    <button @click="themeColor='blue'">蓝色</button>
    <button @click="themeColor='orange'">橘黄色</button>

    <hr />
    <com-son ref="comRef" />

    <com-refdom />
  </div>
</template>

<script>
// import SetUpCom from './components/01.setup'
// import ComRef from './components/02.ref'
// import ComToRefs from './components/03.toRefs'
// import ComComputed from './components/04.computed'
// import ComWatch1 from './components/05.watch-01'
// import ComWatch2 from './components/06.watch-02'
// import ComWatch3 from './components/07.watch-03'
import ComSon from './components/08.son'
import ComRefDom from './components/10.refDom'
import { provide, ref } from '@vue/composition-api'

export default {
  name: 'app',
  components: {
    // 'com-setup': SetUpCom,
    // 'com-ref': ComRef,
    // 'com-torefs': ComToRefs,
    // 'com-computed': ComComputed,
    // 'com-watch1': ComWatch1,
    // 'com-watch2': ComWatch2,
    // 'com-watch3': ComWatch3,
    'com-son': ComSon,
    'com-refdom': ComRefDom
  },
  setup () {
    // 定义 ref 响应式数据
    const themeColor = ref('red')

    // 2. App 根组件作为父级组件，通过 provide 函数向子级组件共享数据（不限层级）
    //    provide('要共享的数据名称', 被共享的数据)
    provide('globalColor', themeColor)

    const comRef = ref(null)

    const showCom = () => {
      console.log(comRef)
      console.log('str1的值是     ' + comRef.value.str1)
      comRef.value.setStr()
    }

    // setup 中 return 数据供当前组件的 Template 使用
    return {
      themeColor,
      comRef,
      showCom
    }
  }
}
</script>

<style lang="scss">
</style>
