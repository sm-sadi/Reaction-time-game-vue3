<template>
    <div class="block" v-if="showbblocks" @click="stopTimer">
       <h1>click this box</h1> 
    </div>
</template>

<script>
// import Block fromn
export default {
props: ['delay'],
data(){
    return{
        showbblocks :false,
        timer : null,
        reactionTime : 0
    }
},
mounted(){
    // console.log("block component just mounted");
    setTimeout(()=>{
        this.showbblocks = true
        this.startTimer();
        // console.log(this.delay);
    }, this.delay)
    
},
// updated(){
//     console.log("updated");
// },
// unmounted(){
//     console.log("block unmounted ");
// }
methods :{
 startTimer(){
     this.timer =setInterval(()=>{
         this.reactionTime +=10
     }, 10)
 },
 stopTimer(){
     clearInterval(this.timer)
    //  console.log(this.reactionTime);
     this.$emit('end', this.reactionTime)
 }
}
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: crimson;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
.block h1{
    color: white;
}
</style>