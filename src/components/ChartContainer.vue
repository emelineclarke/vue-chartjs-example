<template>
  <div class="container">
    <BarChart
      v-if="loaded"
      :chartdata="chartdata"
      :options="{
            scales : {
                xAxes : [ {
                    gridLines : {
                        display : false
                    }
                } ],
                yAxes: [{
                    ticks: {
                        stepSize: 10
                    }
                }]
            }
      }"/>
  </div>
</template>

<script>
import BarChart from './BarChart.vue'
import axios from 'axios'

export default {
  name: 'BarChartContainer',
  components: { BarChart },
  data: () => ({
    loaded: false,
    chartdata: null
  }),
  async mounted () {
    this.loaded = false
    try {
      const json = await axios.get("./users.json");
      var colors = ['rgba(0,184,148,1.0)', 'rgba(108,92,231,1.0)', 'rgba(253,203,110,1.0)', 'rgba(116,185,255,1.0)', 'rgba(255,118,117,1.0)', 'rgba(9,132,227,1.0)']
      var labels = json.data.map(function(d) {return d['Time Period']});
      var models = Object.keys(json.data[0]);
      var datasets = [];
      for (const [model, name] of Object.entries(models)) {
        datasets.push({
            label: name,
            data: json.data.map(function(d) {return d[name]}),
            backgroundColor: colors[model]
        });
      }
      this.chartdata = {labels, datasets};
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>