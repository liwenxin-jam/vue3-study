<template>
  <div>
    <p>当前的count值为：{{count}}</p>
    <button @click="increment">+1</button>
  </div>
</template>

<script>
import { toRefs, reactive } from '@vue/composition-api'

export default {
  setup () {
    // 定义响应式数据对象
    const state = reactive({
      count: 0,
      name: 'xx'
    })

    // 定义页面上可用的事件处理函数
    const increment = () => {
      state.count++
    }

    // return {
    //   ...state, // 被展开后不再是响应式，只是普通对象属性，是个固定值
    //   increment
    // }

    // 在 setup 中返回一个对象供页面使用
    // 这个对象中可以包含响应式的数据，也可以包含事件处理函数
    return {
      // 将 state 上的每个属性，都转化为 ref 形式的响应式数据
      ...toRefs(state),
      // 自增的事件处理函数
      increment
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
