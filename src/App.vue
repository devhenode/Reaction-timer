<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame   " />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
     isPlaying: false,
     delay: null,
     score: null    
    }
  },
  methods: {
      start() {
        this.delay = 2000 + Math.random() * 5000
        this.isPlaying = true
        console.log(this.delay)
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
  font-family: Avenir, Arial, Helvetica, sans-serif;
  text-align: center;
  color: #0f0d0d;
  margin-top: 10px;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
