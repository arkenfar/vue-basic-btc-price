<template>
    <div>
        <div class="apidata">
            <h2 id="title">{{titleFull}}</h2>
            <h3 id="subtitle">{{subtitle}}</h3>
            <hr>
        <div v-if="apiData !== null">

        <p id="btcPrice">{{showApiData.chartName}} : {{showApiData.bpi.USD.rate}} - {{showApiData.bpi.USD.code}}</p>        
        </div>
        <div v-else>
            Loading data...
        </div>
        </div>
        
    </div>
</template>
<script>
export default {
    name: "Alex",
    props: ["title", "apiData", "subtitle"],   
    computed: {
        titleFull(){
            return this.calculateTitle(this.title)
        },
        showApiData(){
            return this.apiData.data
        }
    },

    methods: {
        calculateTitle(title) {
            if (title.length > 0) {
                const titleResult = title.toUpperCase();
                return titleResult
            }else{
                return "No Title"
            }
        }
    }
}
</script>

<style lang="css" scoped>

#title {
    background-color: dodgerblue;
}
#subtitle {
    background-color:dodgerblue;
    
}
#btcPrice {
    font-size: 25px;
}
.apidata {
    border: 15px solid rgb(13, 86, 113) !important;
    padding: 5px
}

</style>