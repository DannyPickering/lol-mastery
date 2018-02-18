<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data () {
    return {
      apiURL: '/api/lol/summoner/v3/summoners/by-name/omnisyntax?api_key=',
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
