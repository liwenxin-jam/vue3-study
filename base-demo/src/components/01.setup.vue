<template>
  <div>
    <p>当前的 count 值为：{{count}}</p>
    <button @click="count+=1">+1</button>
  </div>
</template>

<script>
// 等价于 vue 2.x 中的 Vue.observable() 函数，vue 3.x 中提供了 reactive() 函数，用来创建响应式的数据对象
import { reactive } from '@vue/composition-api'

export default {
  // 在 props 中定义当前组件允许外界传递过来的参数名称，不声明，在setup无法看到
  props: {
    p1: String
  },
  beforeCreate () {
    console.log('beforeCreate')
  },
  // setup 函数会在 beforeCreate 之后、created 之前执行
  // setup 函数的第一个形参，接收 props 数据
  // setup 函数的第二个形参是一个上下文对象，这个上下文对象中包含了一些有用的属性，这些属性在 vue 2.x 中需要通过 this 才能访问到

  setup (props, ctx) {
    console.log('setup')
    // console.log(props.p1)
    // 注意：在 setup() 函数中无法访问到 this
    // console.log(this)
    // context上下文替代了this，通过类似ctx.attrs访问
    // console.log(ctx)

    // 创建响应式数据对象，得到的 state 类似于 vue 2.x 中 data() 返回的响应式对象
    const state = reactive({ count: 0 })
    console.log(state)

    // 想提供给页面使用，必须return出去
    return state
  },
  created () {
    console.log('created')
  }
}
</script>

<style lang="scss" scoped>
</style>
