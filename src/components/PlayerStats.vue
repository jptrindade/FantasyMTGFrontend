<template>
    <div id="player-stats">
        <div class="player" v-for="player in players" :key="player.name">
            <Player :player="player" />
        </div>
    </div>
</template>

<script>
import Player from './Player.vue'
import axios from 'axios'

export default {
    name: "PlayerStats"   ,
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
            .then(response => this.players = response.data.sort( (a, b) => (a.points > b.points) ? -1 : 1))
            .catch(error => {
              console.log(error)
            })
    }
}
</script>

<style scoped>
#player-stats {
    display: flex;
    flex-wrap: wrap;
}
.player {
    margin:auto
}
</style>