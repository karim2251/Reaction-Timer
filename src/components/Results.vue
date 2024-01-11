 <template>
  <p class="result"> Reaction Time : {{ score }} ms</p>
    <p class="rank" ref="rank">{{ rank }}</p>
</template>

<script>
export default {
   props: ['score'],
    data(){
         return{
            rank: null
         }
    },
    mounted(){
        if(this.score < 250){
            this.rank = 'Pro . Good Job';
        }else if(this.score < 400){
            this.rank = 'Average';
            this.$refs.rank.style.color = 'wheat';
        }else{
            this.rank = 'Noob u poor';
            this.$refs.rank.style.color = 'red';

        }
    }
}
</script>

<style scoped>

.rank{
    font-size: 20px;
    color: #4CAF50;
    text-align: center;
    font-weight: bold;
}
.result{
    color:rgb(255, 255, 255);
}

</style>