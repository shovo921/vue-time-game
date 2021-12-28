<template>

  <h1 >Timer Reaction</h1>
   <div v-if="isPlaying">
    <label for=""> please enter your name</label>
  <input type="text" :v-model="name">
   </div>

<button @click="start" :disabled="isPlaying"> Click Here </button>
<h3 v-if="isPlaying"> Please wait: {{waitTime}} Sec</h3>
<p>{{score}}</p>
<Block v-if="isPlaying" :delay="delay" @end="endgame"> </Block> 
<Result :score="score" :name="name" v-if="scoreShow" /> 
</template>

<script>

import Block from './components/Block.vue'
import Result from './components/Result.vue'
export default {
  name: 'App',
  components: {Block ,Result},
 
  data(){
    return{
        isPlaying:false,
        delay:null,
        waitTime:0,
        score:0,
        scoreShow:false,
        name:null
        
    }
  },
  methods:{
    start(){
        this.isPlaying= true
         this.delay=2000 + Math.random()*5000
         this.waitTime = Math.floor((this.delay/1000) % 60);
         this.scoreShow=false
    },
    endgame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.scoreShow=true
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
