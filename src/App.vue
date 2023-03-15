<template>
  <div>
    <h1>Ninja Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">PLAY</button>
    <block v-if="isPlaying" :delay="delay" @end="endGame" />
    <!-- <p v-if="showResult">Reaction Time : {{ score }}</p> -->
    <result v-if="showResult" :score="score" />
  </div>
</template>

<script>
/* eslint-disable */
import Block from './components/Block.vue'
import ResultDisplay from './components/Result.vue'

export default {
  /* eslint-disable */
  name: 'App',
  components: {
    'block': Block,
    'result': ResultDisplay
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
