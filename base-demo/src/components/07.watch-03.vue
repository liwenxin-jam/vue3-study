<template>
  <div>
    <input type="text" v-model="keywords" />
  </div>
</template>

<script>
import { ref, watch, onMounted, onUpdated, onUnmounted } from '@vue/composition-api'

export default {
  setup () {
    // 新版的生命周期函数，可以按需导入到组件中，且只能在 setup() 函数中使用
    // beforeCreate -> use setup()
    // created -> use setup()
    // beforeMount -> onBeforeMount
    // mounted -> onMounted
    // beforeUpdate -> onBeforeUpdate
    // updated -> onUpdated
    // beforeDestroy -> onBeforeUnmount
    // destroyed -> onUnmounted
    // errorCaptured -> onErrorCaptured
    onMounted(() => {
      console.log('mounted!')
    })
    onUpdated(() => {
      console.log('updated!')
    })
    onUnmounted(() => {
      console.log('unmounted!')
    })

    // 定义响应式数据 keywords
    const keywords = ref('')

    // 异步任务：打印用户输入的关键词
    const asyncPrint = val => {
      // 延时 1 秒后打印
      return setTimeout(() => {
        console.log(val)
      }, 1000)
    }

    // 定义 watch 监听
    watch(
      keywords,
      (keywords, prevKeywords, onCleanup) => {
        // 执行异步任务，并得到关闭异步任务的 timerId
        const timerId = asyncPrint(keywords)

        // 如果 watch 监听被重复执行了，则会先清除上次未完成的异步任务
        onCleanup(() => clearTimeout(timerId))
      },
      // watch 刚被创建的时候不执行
      { lazy: true }
    )

    // 把 template 中需要的数据 return 出去
    return {
      keywords
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
