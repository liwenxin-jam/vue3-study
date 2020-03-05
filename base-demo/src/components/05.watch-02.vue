<template>
  <div>
    <p>count {{refCount}}</p>
    <button @click="stopWatch">停止监视</button>
  </div>
</template>

<script>
import { ref, watch } from '@vue/composition-api'

export default {
  setup () {
    const refCount = ref(0)

    // 创建监视，并得到 停止函数
    const stop = watch(() => {
      console.log('监听到了 refCount 的变化')
      console.log(refCount.value)
    })

    const stopWatch = () => {
      // 调用停止函数，清除对应的监视
      stop()
    }

    setTimeout(() => {
      refCount.value += 1
    }, 3000)

    return {
      refCount,
      stopWatch
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
