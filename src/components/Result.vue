<template>
  <h1 >{{name}} you are {{result}} </h1>
</template>

<script>
export default {
props:['score,name'],
data(){
    return{
        result:null
    }
},

   mounted(){
     if (this.score < 500) {
       this.result='you are win' 
      
     }
     else{
         this.result='you are loser' 
       
     }
} ,

}

</script>

<style>

</style>