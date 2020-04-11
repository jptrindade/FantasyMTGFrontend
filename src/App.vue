<template>
  <div id="app">

    <div v-for="player in players" :key="player.name">
      <Player :player="player" />
    </div>
  </div>
</template>

<script>
import Player from './components/Player.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Player
  },
  data (){
    return {
      players: []
    }
  } ,
    mounted (){
        axios.get(process.env.VUE_APP_DATABASE + 'players')
            .then(response => this.players = response.data)
            .catch(error => {
              console.log(error)
            })
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
