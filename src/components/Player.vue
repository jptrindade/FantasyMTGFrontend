<template>
    <div>
        {{player.name}} has {{points}} points
        <div v-for="pick in player.picks" :key="player.name + pick">
            <p>
                {{pick}}
            </p>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: "Player"   ,
    props: ["player"],
    data (){
        return{
            points: 0
        }
    },
    mounted (){
        axios.get(process.env.VUE_APP_DATABASE + 'stats/'+this.player.name)
            .then(response => this.points = response.data.points)
            .catch(error => {
              console.log(error)
            })
    }
}
</script>

<style scoped>

</style>