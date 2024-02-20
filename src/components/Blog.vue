<template>
  <div class="blog" v-if="showBlog" @click="stop">
    <h1>Click Here </h1>

  </div>
</template>

<script>
export default {
 props:['delay'],
 data(){
    return{
        showBlog:false,
        score:0,
        timer:null
    }
 },
 mounted(){
  setTimeout(() => {
    return this.showBlog=true,
           this.startTimer()  
  }, this.delay);
 },
 methods:{
   startTimer(){
     this.timer= setInterval(() => {
         this.score+=50
     }, 50);
   },
   stop(){
    clearInterval(this.timer),
    this.$emit("endGame",this.score)
    

   }
 }
}
</script>

<style>
.blog{
    background-color: aquamarine;
    width: 400px;
    height: 300px;
    margin: 20px auto;
    padding-top: 10px;

}
</style>