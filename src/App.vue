<template>
  <div id="app">
      <TopBarChart />
      <PlayerStats />

  </div>
</template>

<script>
import PlayerStats from './components/PlayerStats.vue'
import TopBarChart from './components/TopBarChart.vue'

export default {
  name: 'App',
  components: {
    TopBarChart,
    PlayerStats
  }
    
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
