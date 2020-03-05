<template>
  <div>
    <h3>子组件</h3>
    <p>{{str1}}</p>
    <hr />
    <com-grandson />
  </div>
</template>

<script>
import { ref } from '@vue/composition-api'
import ComGrandson from './09.grandson'

export default {
  components: {
    'com-grandson': ComGrandson
  },
  setup () {
    const str1 = ref('this is 子组件')

    const setStr = () => {
      str1.value = '被赋值啦~~~~~'
    }

    return {
      str1,
      setStr
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
