<template>
  <div>
    <BarChart
      :title="sector"
      :series="data"
      :summary="summary"
      :key="index"
      v-for="({sector, summary, data}, index) in series"
    />
  </div>
</template>

<script>

import BarChart from '@/components/BarChart'

export default {
  name: 'BarChartList',
  props: ['series', 'title'],
  components: { BarChart }
}
</script>
