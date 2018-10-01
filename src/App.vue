<template>
  <div id="app">
    <h2>Area chart</h2>
    <AreaChart :timeSeries="timeSeries" />

    <h2>Bar chart</h2>
    <BarChart :series="categorySeries" />
  </div>
</template>

<script>
import { AreaChart, BarChart } from '@/components'
import timeSeries from "@/data/timeSeries.js"
import categorySeries from "@/data/categorySeries.json"

export default {
  name: 'app',
  components: {
    AreaChart,
    BarChart
  },
  data () {
    return { timeSeries, categorySeries }
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
