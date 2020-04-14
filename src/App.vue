<template id="global">
  <div id="app">
      <Snapshot />
      <TopBarChart  :showTop="20"/>
      <PlayerStats />
  </div>
</template>

<script>
import PlayerStats from './components/PlayerStats.vue'
import TopBarChart from './components/TopBarChart.vue'
import Snapshot from './components/Snapshot.vue'

export default {
  name: 'App',
  components: {
    TopBarChart,
    PlayerStats,
    Snapshot
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
#global{
  background:"#eeeeee"
}
</style>
