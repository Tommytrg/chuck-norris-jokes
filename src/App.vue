<template>
  <div id="app">
    <h1>CHUCK NORRIS JOKE GENERATOR</h1>

      <div>
        <p>{{ joke }}</p>
      </div>

      <button @click="getJoke">
        Generate Joke!
      </button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      joke: 'Loading...',
    };
  },
  created() {
    axios
      .get('https://api.chucknorris.io/jokes/random')
      .then((response) => {
        this.joke = response.data.value;
      })
      .catch(() => {
        this.joke = 'Oops, it seems to be a problem. Retry in a fex seconds';
      });
  },
  methods: {
    getJoke() {
      axios
      .get('https://api.chucknorris.io/jokes/random')
      .then((response) => {
        this.joke = response.data.value;
      })
      .catch(() => {
        this.joke = 'Oops, it seems to be a problem. Retry in a fex seconds';
      });
    },
  },

};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  padding: 0 2em;
}
</style>
