<template>
  <div>
    <!-- 注意：自动会访问.value属性取值，跟在setup中访问不同 -->
    <p>当前的 count 值为：{{count}}</p>
    <button @click="count+=1">+1</button>
  </div>
</template>

<script>
// ref() 函数用来根据给定的值创建一个响应式的数据对象，ref() 函数调用的返回值是一个对象，这个对象上只包含一个 .value 属性
import { reactive, ref } from '@vue/composition-api'

export default {
  setup () {
    // // 创建响应式数据对象 count，初始值为 0
    // const count = ref(0)

    // // 如果要访问 ref() 创建出来的响应式数据对象的值，必须通过 .value 属性才可以
    // console.log(count.value) // 输出 0
    // // 让 count 的值 +1
    // count.value++
    // // 再次打印 count 的值
    // console.log(count.value) // 输出 1

    // 当把 ref() 创建出来的响应式数据对象，挂载到 reactive() 上时，会自动把响应式数据对象展开为原始的值，不需通过 .value 就可以直接被访问
    const count = ref(0)
    const state = reactive({
      count
    })

    console.log(state.count) // 输出 0
    state.count++ // 此处不需要通过 .value 就能直接访问原始值
    console.log(count) // 输出 1

    // 注意：新的 ref 会覆盖旧的 ref
    // 创建 ref 并挂载到 reactive 中
    const c1 = ref(0)
    const state2 = reactive({
      c1
    })

    // 再次创建 ref，命名为 c2
    const c2 = ref(9)
    // 将 旧 ref c1 替换为 新 ref c2
    state2.c1 = c2
    state2.c1++

    console.log(state2.c1) // 输出 10
    console.log(c2.value) // 输出 10
    console.log(c1.value) // 输出 0

    // isRef() 用来判断某个值是否为 ref() 创建出来的对象；应用场景：当需要展开某个可能为 ref() 创建出来的值的时候
    // const unwrapped = isRef(foo) ? foo.value : foo

    // 跟reactive一样，需要return出去才能组模板使用
    return {
      count
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
