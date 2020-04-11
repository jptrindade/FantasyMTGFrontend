<template>
    <div>
        <div v-for="player in players" :key="player.name">
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
            .then(response => this.players = response.data)
            .catch(error => {
              console.log(error)
            })
    }
}
</script>

<style scoped>

</style>