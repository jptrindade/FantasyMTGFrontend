<template>
    <div>
        
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
        axios.get(process.env.VUE_APP_DATABASE + 'stats/IKO')
            .then(response => this.stats = response.data[0].stats)
            .catch(error => {
              console.log(error)
            })
    }
}
</script>

<style scoped>

</style>