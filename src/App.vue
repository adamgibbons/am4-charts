<template>
  <div id="app">
    <AreaChart />
  </div>
</template>

<script>
import AreaChart from './components/AreaChart.vue'

export default {
  name: 'app',
  components: {
    AreaChart
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /*color: white;*/
  margin-top: 60px;
  /*background-color: #222222;*/
}
</style>
