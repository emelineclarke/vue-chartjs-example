<template>
  <div id="app">
    <MainContent msg="Dashboard"/>
    <BarChartContainer />
  </div>
</template>

<script>
import MainContent from './components/MainContent.vue'
import BarChartContainer from './components/ChartContainer.vue'

export default {
  name: 'app',
  components: {
    MainContent,
    BarChartContainer
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
