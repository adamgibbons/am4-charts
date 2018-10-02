<template>
  <div id="app" class="wrapper">
    <div class="column">
      <BarChart :series="categorySeries" title="Bar Chart" />
    </div>
    <div class="column">
      <AreaChart :series="timeSeries" title="Area Chart" />
    </div>
  </div>
</template>

<script>
import { AreaChart, BarChart } from '@/components'
import timeSeries from "@/data/timeSeries.js"
import categorySeries from "@/data/categorySeries.json"

export default {
  name: 'app',
  components: { AreaChart, BarChart },
  data () {
    return { timeSeries, categorySeries }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}
.wrapper {
  display: block;
}
.column {
  display: inline-block;
  margin: 1rem;
}
.chart {
  /*width: 100%;*/
  width: 500px;
  height: 300px;
}
</style>
