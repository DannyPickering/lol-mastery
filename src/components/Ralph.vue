<template>
  <div class ="header">
      <div class = "header-main">
        <div class="input-bar">
            <input class="summoner-name-input" v-model="summonerName" placeholder="Summoner Name" v-on:keyup.enter="submitName">
        </div>
      </div>
  </div>
</template>

<script>
import axios from 'axios'
const env = require('../../.env.json')

export default {
  name: 'Ralph',
  data () {
    return {
      apiURL: '/api/lol/summoner/v3/summoners/by-name/' + this.summonerName + '?api_key=' + env.riot.API_KEY,
      results: [],
      summonerName: ''
    }
  },
  methods: {
    submitName () {
      axios.get(this.apiURL).then(response => { this.results = response })
    }
  }
}
</script>

<style media="screen">

  body {
    font-family: serif;
    background: rgb(64, 58, 166);
  }

  #app {
    padding-top: 100px;
  }

  .input-bar {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    align-content: flex-end;
    padding-top: 50px;
    width: 50%;
  }

  .summoner-name-input {
    margin: 0;
    display: flex;
    position: relative;
    flex: 1 1 auto;
    margin-bottom: 0;
    width: 100%;

    background: rgb(64, 58, 166);
    border: 1px solid rgba(0, 0, 0, 0.4);
    border-bottom-color: rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 12px -2px rgba(0, 0, 0, 0.3);
    font-weight: 300;
    color: #cfd936;
    border-radius: 4px;
    padding: 1.5em 1.5em !important;

  }

  .summoner-name-input::placeholder {
    font-weight: 520;
    font-size: 1.1rem;
    color: #757091;
    cursor: text;

  }

  .header-main {
    margin-top: 150px;
    max-width: 900px;
    margin-left: auto;
    margin-right: auto;
    display: flex;
    justify-content: center;
    padding-left: 15px;
    padding-right: 15px;

  }

</style>
