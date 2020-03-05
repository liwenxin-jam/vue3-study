<template>
  <div id="app">
    <!-- <com-setup p1="aaaaaaa" /> -->
    <!-- <com-ref /> -->
    <!-- <com-torefs /> -->
    <com-computed />
  </div>
</template>

<script>
// import SetUpCom from './components/01.setup'
// import ComRef from './components/02.ref'
// import ComToRefs from './components/03.toRefs'
import ComComputed from './components/04.computed'

export default {
  name: 'app',
  components: {
    // 'com-setup': SetUpCom,
    // 'com-ref': ComRef,
    // 'com-torefs': ComToRefs,
    'com-computed': ComComputed
  }
}
</script>

<style lang="scss">
</style>
