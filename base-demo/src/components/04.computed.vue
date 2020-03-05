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
    // 创建一个 ref 响应式数据
    const count = ref(1)

    // 根据 count 的值，创建一个响应式的计算属性 plusOne
    // 它会根据依赖的 ref 自动计算并返回一个新的 ref
    const plusOne = computed(() => count.value + 1)

    console.log(plusOne.value) // 输出 2
    // plusOne.value++ // error

    return {
      count,
      plusOne
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
