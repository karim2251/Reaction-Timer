<template>
  <h1>
      Reaction timer :)
  </h1>
  <p>You have to press when you see the block as soon possible??</p>
  <button @click="start" :disabled="isPlaying" id="playbtn" type="button">
    {{btnTitle}}
  </button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResult" :score="score"/>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default{
  components:{
    Block,
    Results
  },
  data(){
    return{
      btnTitle: 'Play',
      isPlaying: false,
      showResult: false,
      delay: null,
      score: null
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 4000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
      this.btnTitle = 'Play Again';
    }
  }

}

</script>

<style scoped>
#playbtn{
  background-color: #4CAF50;
  border: none;
  border-radius: 20px;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}
#playbtn:hover{
  background-color: #3e8e41;
}
#playbtn:disabled{
  opacity: 0.6;
  cursor: not-allowed;
}
p{
  color: wheat;
}
</style>