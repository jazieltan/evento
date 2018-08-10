<template>
  <div id="app">
    <SetDate />
  </div>
</template>

<script>
import SetDate from './components/SetDate.vue'
export default {
  name: 'app',
  components: {
    SetDate
  }
}
</script>

<style lang="scss">


#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 100%;
}
</style>
