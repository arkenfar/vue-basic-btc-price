<template>
  <div id="app" class="appDiv">    
    <Alex title="Bitcoin Price" :apiData="apiData" subtitle="updates every 10 sec"/>
  </div>
</template>

<script>
import Alex from '@/components/Alex';
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Alex
  },
  data() {
    return {
      apiData: null
    }
  },
  mounted() {
      setInterval(() => {
        /* ignore-console on next line */
        console.log("Starting api call to coindesk")
        axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then((response) => {
        this.condeskData = response
        console.log("Data from Api call: ", response.data)
        })
      }, 10000);
  },
  computed: {
    condeskData: {
      get(){
        return this.apiData
      },
      set(value){
        this.apiData = value
      }
    }
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Stalinist+One&display=swap');
</style>
<style>
#app {
  font-family: 'Stalinist One', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
