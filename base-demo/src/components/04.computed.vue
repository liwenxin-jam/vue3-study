<template>
  <div>
    <p>当前的count值为：{{count}}</p>
    <p>计算属性的值为：{{plusOne}}</p>

    <button @click="count+=1">+1</button>
  </div>
</template>

<script>
import { ref, computed } from '@vue/composition-api'

export default {
  setup () {
    // // 创建一个 ref 响应式数据
    // const count = ref(1)

    // // 根据 count 的值，创建一个响应式的计算属性 plusOne
    // // 它会根据依赖的 ref 自动计算并返回一个新的 ref
    // const plusOne = computed(() => count.value + 1)

    // console.log(plusOne.value) // 输出 2
    // // plusOne.value++ // error ，默认只是可读不可写

    // 创建一个 ref 响应式数据
    const count = ref(1)

    // 创建一个 computed 计算属性
    const plusOne = computed({
      // 取值函数
      get: () => count.value + 1,
      // 赋值函数
      set: val => {
        count.value = val - 1
      }
    })

    // 为计算属性赋值的操作，会触发 set 函数
    plusOne.value = 9
    // 触发 set 函数后，count 的值会被更新
    console.log(count.value) // 输出 8

    return {
      count,
      plusOne
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
