<template>
    <div>
        <h1> {{player.name}}</h1>
        <h2> {{this.points}} points</h2>
        <h2> Picks </h2>
        <div v-for="pick in this.picks_display" :key="player.name + pick.card">
            <p>
                {{pick.card}} {{pick.points}}
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
            picks_display: [],
            points: 0
        }
    },
    mounted (){
        axios.get(process.env.VUE_APP_DATABASE + 'stats/'+this.player.name)
            .then(response => {
                this.player.picks.forEach(element => {
                    this.picks_display.push({
                        card: element,
                        points: response.data[element]
                    })
                });
                this.picks_display.sort( (a, b) => (a.points > b.points) ? -1 : 1)
                this.points = response.data.points
                }
            )
            .catch(error => {
              console.log(error)
            })
    }
}
</script>

<style scoped>

</style>