<template>
  <div class="flex-row">
    <div class="flex-row-item">
      <div class="label-percentage">{{summary}}%</div>
      <div class="label-sector">Sector: {{title}}</div>
    </div>
    <div class="flex-row-item">
      <div class="chart" ref="chartdiv">
      </div>
    </div>
  </div>
</template>

<script>

import * as am4core from "@amcharts/amcharts4/core"
import * as am4charts from "@amcharts/amcharts4/charts"
import COLORS from '@/data/colors'

export default {
  name: 'BarChart',
  props: ['series', 'title', 'summary'],
  mounted() {
    var chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart)

    chart.data = this.series


    var categoryAxis = chart.yAxes.push(new am4charts.CategoryAxis())
    categoryAxis.renderer.grid.template.location = 0
    categoryAxis.dataFields.category = "country"
    categoryAxis.renderer.minGridDistance = 20
    categoryAxis.renderer.minWidth = 120

    var valueAxis = chart.xAxes.push(new am4charts.ValueAxis())
    valueAxis.renderer.maxLabelPosition = 0.98  

    var series = chart.series.push(new am4charts.ColumnSeries())
    series.dataFields.categoryY = "country"
    series.dataFields.valueX = "prevalence"
    series.tooltipText = "{valueX.value}"
    // series.sequencedInterpolation = true
    // series.defaultState.transitionDuration = 1000
    // series.sequencedInterpolationDelay = 100
    series.columns.template.strokeOpacity = 0
    series.columns.template.fill = COLORS.orange

    chart.cursor = new am4charts.XYCursor()

    // as by default columns of the same series are of the same color, we add adapter which takes colors from chart.colors color set
    // series.columns.template.adapter.add("fill", (fill, target) => {
    //   return chart.colors.getIndex(target.dataItem.index)
    // });
  },
  beforeDestroy() {
    if (this.chart) {
      this.chart.dispose();
    }
  }
}
</script>

