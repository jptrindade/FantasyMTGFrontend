<template>
  <div id="app">
    <CardLeaderboard />
    <PlayerStats />
  </div>
</template>

<script>
import PlayerStats from './components/PlayerStats.vue'
import CardLeaderboard from './components/CardLeaderboard.vue'

export default {
  name: 'App',
  components: {
    CardLeaderboard,
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
