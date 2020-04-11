<template>
    <div>
        <div v-for="stat in stats" :key="stat.card">
            {{stat.card}} {{stat.points}}
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: "CardLeaderboard"   ,
    data (){
        return {
            stats: []
        }
    } ,
    mounted (){
        axios.get(process.env.VUE_APP_DATABASE + 'stats/filter/MatosFilter')
            .then(response => this.stats = response.data.sort( (a, b) => (a.points > b.points) ? -1 : 1))
            .catch(error => {
              console.log(error)
            })
    },
    methods: {
        
    }
}
</script>

<style scoped>

</style>