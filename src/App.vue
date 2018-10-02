<template>
  <div id="app">
    <div class="column">
      <BarChartList :series="apiCall" title="Bar Chart" />
    </div>
    <div class="column">
      <AreaChart :series="timeSeries" title="Area Chart" />
    </div>
  </div>
</template>

<script>
import { AreaChart, BarChartList } from '@/components'
import timeSeries from "@/data/timeSeries.js"
import apiCall from "@/data/apiCall.json"

export default {
  name: 'app',
  components: { AreaChart, BarChartList },
  data () {
    return { timeSeries, apiCall }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}
.column {
  display: inline-block;
  vertical-align: top;
}
.chart {
  /*width: 100%;*/
  width: 470px;
  height: 230px;
}
.flex-row {
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  vertical-align: 
}
.flex-row-item {
}
.label-percentage {
  font-size: 2rem;
  border: 1px solid #bbb;
  padding: 0;
  margin: 0 0 .1em;
}
.label-sector {
  font-size: .8rem;
  text-transform: uppercase;
  font-style: oblique;
}
</style>
