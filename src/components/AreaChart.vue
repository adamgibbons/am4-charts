<template>
  <div class="chart" ref="chartdiv">
  </div>
</template>

<script>

import * as am4core from "@amcharts/amcharts4/core"
import * as am4charts from "@amcharts/amcharts4/charts"
import COLORS from '@/data/colors'

export default {
  name: 'AreaChart',
  props: ['timeSeries'],
  mounted() {
    // Create chart instance
    let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);

    // Add data
    chart.data = this.timeSeries

    // Create axes
    chart.xAxes.push(new am4charts.DateAxis())
    chart.yAxes.push(new am4charts.ValueAxis());

    // Create series
    let series = chart.series.push(new am4charts.LineSeries());
    series.fillOpacity = 1;
    series.fill = COLORS.brown,
    series.name = "Units";
    series.stroke = am4core.color(COLORS.orange);
    series.strokeWidth = 3;
    series.dataFields.valueY = "prevalence";
    series.dataFields.dateX = "date";
  },
  beforeDestroy() {
    if (this.chart) {
      this.chart.dispose();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.chart {
  width: 100%;
  height: 500px;
}
</style>