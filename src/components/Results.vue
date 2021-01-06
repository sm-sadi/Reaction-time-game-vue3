<template>
  <div>
      <h1> your scrore is  : {{score}}</h1>
      <p> {{rank}}</p>
  </div>
</template>

<script>
export default {
    props: ['score'],
data(){
    return{
        rank :null
    }
    
    },
    mounted(){
       if(this.score <250){
          this.rank = "you are fast"  
        }else if(this.score < 400){
            this.rank =" not bad"
        }else{
            this.rank = " you are slow"
        } 

}
}
</script>

<style>

</style>