<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h3> Click here </h3>
    <p>Time Flies Quickly!!</p>
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        console.log('mounted');
        setTimeout(()=>{
            this.showBlock = true;
            this.startTimer();
        }, this.delay)
    },
    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime+=10;
            },10)
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit('end', this.reactionTime);
        }
    }
  
}
</script>

<style scoped>
.block{
    max-width:400px;
    background-color: #4CAF50;
    border: none;
    border-radius: 20px;
    color: white;
    padding: 100px 0;
    margin: 20px auto;
    text-align: center;
}
.block p{
color: rgba(29, 28, 28, 0.842);
}
 </style>