<template>
  <div id="app">

    <MainHome />

  </div>
</template>

<script>

import MainHome from './components/MainHome.vue'
export default {
  name: 'App',
  components: {
    MainHome,
  },
}

</script>

<style lang="scss">

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: -8px;
  padding: 0;
  box-sizing: border-box;
}

</style>
