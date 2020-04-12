
<script>
import axios from 'axios'
import { Bar } from 'vue-chartjs'

export default {
    extends: Bar,
    name: "TopBarChart"   ,

    data (){
        return {
            stats: [],
            labels: [],
            datasets: [
                {
                    label: "Fantasy Points",
                    backgroundColor: "#f87979",
                    data : []
                }
            ],
            showTop: 20
        }
        
    } ,
    created (){
        axios.get(process.env.VUE_APP_DATABASE + 'stats/IKOrmNoLands')
            .then(response => {
                this.stats = response.data.sort( (a, b) => (a.points > b.points) ? -1 : 1)
                this.stats.slice(0,this.showTop).forEach(element => {
                    this.labels.push(element.card)
                    this.datasets[0].data.push(element.points)
                });
                this.$emit('loading',false)
                this.renderChart({
                    labels: this.labels,
                    datasets: this.datasets
                    },
                     { responsive: true, maintainAspectRatio: false })
                
                })
            .catch(error => {
              console.log(error)
            })
    }
} 




</script>


<style src="vue-d3-barchart/dist/vue-d3-barchart.css"></style>