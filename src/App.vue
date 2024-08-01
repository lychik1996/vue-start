<script >
import Input from './components/Input.vue';
import Selector from './components/Selector.vue';
import CryptoConvert from 'crypto-convert';
import Favorite from './components/Favorite.vue';

const convert = new CryptoConvert();
export default{
  components:{Input, Selector,Favorite},
  data(){
    return{
      amount:0,
      cryptoFirst:'',
      cryptoSecond:'',
      error:'',
      result:0,
      favs:[]
    }
  },
  methods:{
    favorite(){
       if(this.cryptoFirst===this.cryptoSecond && this.cryptoFirst && this.cryptoSecond){
        this.error = "Select different currencies";
        this.result=0;
        return
      } else if(this.cryptoFirst ==="" || this.cryptoSecond===""){
        this.error="Select two currencies";
        this.result=0;
        return
      }
      this.favs.push({
        from:this.cryptoFirst,
        to:this.cryptoSecond
      })
    },
    getFromFavs(index){
      this.cryptoFirst=this.favs[index].from;
      this.cryptoSecond=this.favs[index].to;
    },
    changeAmount(val){
      this.amount=val
    },
    setCryptoFirst(val){
      this.cryptoFirst=val
    },
    setCryptoSecond(val){
      this.cryptoSecond=val
    },
     async convert(){
      if(this.amount<=0){
        this.error='Enter a number greater than zero';
        this.result=0;
        return;
      }else if(this.cryptoFirst===this.cryptoSecond && this.cryptoFirst && this.cryptoSecond){
        this.error = "Select different currencies";
        this.result=0;
        return
      } else if(this.cryptoFirst ==="" || this.cryptoSecond===""){
        this.error="Select two currencies";
        this.result=0;
        return
      }
      this.error='';
      await convert.ready();
      
      this.result = convert[this.cryptoFirst][this.cryptoSecond](this.amount);
    }

  }
}
</script>

<template>
  <h1>Crypto</h1>
  <Input :changeAmount="changeAmount" :convert="convert" :favorite="favorite"/>
  <p v-if="error" class="error">{{ error }}</p>
  <p v-if="result" class="result-text">{{ result }}</p>
  <Favorite :favs="favs" :getFromFavs="getFromFavs" v-if="favs.length>0"/>
  <div class="selectors">
    <Selector :setCrypto="setCryptoFirst" :cryptoNow="cryptoFirst"/>
    <Selector :setCrypto="setCryptoSecond" :cryptoNow="cryptoSecond"/>
  </div>
 
</template>

<style scoped>
.selectors{
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 0 auto;
}
.error{
  color: white;
}
.result-text{
  color: white;
  font-size: 2em;
  font-family: 'Nabla',cursive;
}
</style>
