<template>
  <h1>Test Your Reaction</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @reactTime="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactTime) {
      this.score = reactTime
      this.isPlaying = false
      this.showResults = true
    }
  },
}
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: hsla(160, 100%, 37%, 1);
  /* background-color:  hsla(160, 100%, 37%, 0.2); */
}

h1 {
  font-size: 2.3em;
}

button {
  height: 2.5em;
  width: 5.5em;
  background: hsla(160, 100%, 37%, 1);
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px auto auto auto;
  text-transform: capitalize;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}

button:hover {
  background: hsla(160, 100%, 37%, 0.2);
}
</style>
