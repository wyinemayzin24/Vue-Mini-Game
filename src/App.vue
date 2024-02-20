<template>
  
 <h1>Catch Me If U Can :</h1>
 <button @click="start" :disabled="isPlaying" >play</button>
<div v-if="isPlaying">
   <Blog :delay="delay" @endGame="endGame"  />

</div>
 <div v-if="end">
    <Result :score="score"/>
 </div>

</template>

<script>

import Blog from './components/Blog.vue'
import Result from './components/Result.vue'
export default {
  name: 'App',
  
  components: {
    Blog,Result
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:0,
      end:false
    }
  },
  methods:{
          start(){
            return this.isPlaying=true,
                  this.delay=2+Math.random()*5000
                  
              },
           endGame(score){
            this.score=score,
            this.isPlaying=false,
            this.end=true;
        
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
