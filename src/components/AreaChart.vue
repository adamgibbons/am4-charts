<template>
  <div class="chart" ref="chartdiv">
  </div>
</template>

<script>

import * as am4core from "@amcharts/amcharts4/core"
import * as am4charts from "@amcharts/amcharts4/charts"
import timeSeries from "@/data/timeSeries.js"

export default {
  name: 'AreaChart',
  mounted() {
    // Create chart instance
    let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);

    // Add data
    chart.data = timeSeries

    // Create axes
    chart.xAxes.push(new am4charts.DateAxis())
    chart.yAxes.push(new am4charts.ValueAxis());

    // Create series
    let series = chart.series.push(new am4charts.LineSeries());
    series.name = "Units";
    series.stroke = am4core.color("darkorange");
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