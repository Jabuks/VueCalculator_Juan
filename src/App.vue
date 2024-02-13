<template>
  <div id="app">
    <SimpleCalculator/>
  </div>
</template>

<script>
import SimpleCalculator from './components/SimpleCalculator.vue'

export default {
  name: 'app',
  components: {
    SimpleCalculator
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
