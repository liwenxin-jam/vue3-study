<template>
  <div id="app">
    <!-- <com-setup p1="aaaaaaa" /> -->
    <!-- <com-ref /> -->
    <!-- <com-torefs /> -->
    <!-- <com-computed /> -->
    <!-- <com-watch1 /> -->
    <com-watch2 />
  </div>
</template>

<script>
// import SetUpCom from './components/01.setup'
// import ComRef from './components/02.ref'
// import ComToRefs from './components/03.toRefs'
// import ComComputed from './components/04.computed'
// import ComWatch1 from './components/05.watch-01'
import ComWatch2 from './components/05.watch-02'

export default {
  name: 'app',
  components: {
    // 'com-setup': SetUpCom,
    // 'com-ref': ComRef,
    // 'com-torefs': ComToRefs,
    // 'com-computed': ComComputed,
    // 'com-watch1': ComWatch1,
    'com-watch2': ComWatch2
  }
}
</script>

<style lang="scss">
</style>
