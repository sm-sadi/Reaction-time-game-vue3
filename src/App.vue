<template>
  <h1>Click as soon as the box shows up</h1>
  <button @click="start" :disabled="isPlaying">start </button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame"  />
    <!-- <p v-if="showResults"> Your Reaction time: {{score}} ms</p> -->
    <Results v-if="showResults" :score='score' />
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {Block , Results},
  data(){
    return{
      isPlaying: false,
      delay : null,
      score: null,
      showResults : false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random()*5000;
      // console.log(this.delay);
      this.isPlaying =true
      this.showResults =false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults =true
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
