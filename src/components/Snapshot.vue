<script>
import axios from 'axios'
import { Line } from 'vue-chartjs'

export default {
    extends: Line,
    name: "Snapshot"   ,

    data (){
        return {
            stats: [],
            labels: [],
            colors: ['#A7226E','#EC2049','#F26B38','#F7DB4F','#2F9599','#5ac18e'],
            datasets: []
        }
        
    } ,
    created (){
        axios.get(process.env.VUE_APP_DATABASE + 'snapshot/')
            .then(response => {
            if(response.data.length != 0){
                this.snapshots = response.data.sort( (a, b) => (a.date > b.date) ? 1 : -1)
                this.snapshots[0].points.forEach(element => {
                    var backgroundColor = this.colors[0]
                    this.datasets.push({
                        label: element.player,
                        borderColor: backgroundColor, 
                        fill: false,
                        data: []
                    })
                    this.colors.splice(this.colors.indexOf(backgroundColor), 1)
                })
                this.snapshots.forEach(snapshot => {
                    var newdate = snapshot.date.split('-')
                    this.labels.push(newdate[2].split('T')[0]+'-'+newdate[1])
                    for(var i = 0; i< this.datasets.length; i++){
                        this.datasets[i].data.push(snapshot.points[i].points)
                    }
                })

                this.renderChart({
                    labels: this.labels,
                    datasets: this.datasets
                    },
                     { responsive: true, maintainAspectRatio: false })
            }
                })
            .catch(error => {
              console.log(error)
            })
    }
} 




</script>


<style src="vue-d3-barchart/dist/vue-d3-barchart.css"></style>