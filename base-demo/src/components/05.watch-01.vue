<template>
  <div>

  </div>
</template>

<script>
import { watch, ref, reactive } from '@vue/composition-api'

export default {
  setup () {
    // 1. 基本用法
    const count = ref(0)

    // 定义 watch，只要 count 值变化，就会触发 watch 回调
    // watch 会在创建时会自动调用一次
    watch(() => console.log(count.value))
    // watch(() => console.log(count.value), { lazy: false }) // 这里无效
    // 输出 0

    setTimeout(() => {
      count.value++
      // 输出 1
    }, 1000)

    // 2. 监视 reactive 类型的数据源
    // // 定义数据源
    // const state = reactive({ count: 0 })
    // // 监视 state.count 这个数据节点的变化，如果不想要触发初始化watch，可以加上配置 { lazy: true }
    // watch(
    //   // 只能监听reactive某个属性，不能监听整个数据源state，也可以监听ref类型的数据源
    //   () => state.count,
    //   // count是新值，prevCount是旧值
    //   (count, prevCount) => {
    //     console.log(count, prevCount)
    //   },
    //   {
    //     lazy: true
    //   }
    // )

    // setTimeout(() => {
    //   state.count++
    // }, 1000)

    const state = reactive({ count: 0, name: 'zs' })

    // 3. 监视多个数据源，监视 reactive类型会比ref类型麻烦
    watch(
      [() => state.count, () => state.name], // Object.values(toRefs(state)),
      // [count, name], // 需要被监视的多个 ref 数据源
      ([count, name], [prevCount, prevName]) => {
        console.log(count, name) // 新的 count 值 name 值
        console.log('------------')
        console.log(prevCount, prevName) // 旧的 count 值 name 值
      },
      {
        lazy: true // 在 watch 被创建的时候，不执行回调函数中的代码
      }
    )

    setTimeout(() => {
      state.count++
    }, 1000)

    setTimeout(() => {
      state.name = 'xx'
    }, 2000)
  }
}
</script>

<style lang="scss" scoped>
</style>
