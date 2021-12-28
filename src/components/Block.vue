<template>
   <label for=""> please enter your name</label>
   <input type="text" v-model="name">
  <div class="block" v-if="showBlock" @click="stopTime()">
    click me
   
  </div>
  
</template>

<script>
export default {
props:['delay'],
data(){
    return{
        showBlock:false,
        time:null,
        reactionTime:0,
        waitTime:0,
        name:null
    
    }
},
mounted(){
     setTimeout(() =>{
         this.showBlock = true
         this.startTime()
     },  this.delay
     );

    
},
update(){
  
},
unmounted(){
    
},
methods:{
    startTime(){
       this.time=setInterval(()=>{
           this.reactionTime +=10
       },10) 
    },
    stopTime(){
       clearInterval(this.time)
       this.$emit('end',this.reactionTime)

    }
},

}
</script>

<style scoped>
.block{
    padding: auto;
    text-align: center;
    width: 500px;
    margin: auto;
    background: green;
    height: 200px;
    padding: 30px;
    color: white;
    font-size: 20px;
    font-weight: 800;
     border-radius: 96px;
}


</style>