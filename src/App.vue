<template>
  <h1>Ninja Reacton Timer</h1>
  <button @click="start" v-bind:disabled="is_playing">Play</button>
  <Block v-if="is_playing" v-bind:delay="delay" @end_of_game="endGame" />
  <p v-if="show_results">Reaction time: {{ score }} ms</p>
</template>

<script>
import Block from './components/Block.vue'; 
export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      is_playing: false,
      delay: null,
      score: null,
      show_results: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.is_playing = true
      this.show_results = false
    },
    endGame( reaction_time_upon_end_of_game ) {
      this.score = reaction_time_upon_end_of_game
      this.is_playing = false
      this.show_results = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
