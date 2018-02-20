<template>
  <div id="app">
  
    <router-view/>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data () {
    return {
      apiURL: '/api/lol/summoner/v3/summoners/by-name/omnisyntax?api_key=RGAPI-86dbe255-912a-4d3d-b814-58e8afe26e32',
      results: []
    }
  },
  mounted () {
    axios.get(this.apiURL).then(response => { this.results = response })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
