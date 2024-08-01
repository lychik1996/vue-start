<script>
import { current } from '@reduxjs/toolkit';

export default{
 props:{
    setCrypto:{
        type:Function,
        required:true
    },
    cryptoNow:{
        type:String,
    }
 },
 data(){
    return{
        cryptos:['BTC','ETH','USDT'],
        
    }
 },
 
}
</script>

<template>
    <ul>
        <li v-for="(e,i) in cryptos" :key="i" @click="setCrypto(e)" :className="cryptoNow===e?'active':''">{{ e }}</li>
    </ul>
</template>

<style scoped>
ul{
    list-style: none;
    width: 200px;
    padding: 0;
    border-radius: 3px;
    border: 3px solid black;
}
li{
    display: block;
    background: #1A032D;
    color: #fff;
    padding: 20px 0;
}
li:hover{
    background: #24043e;
    cursor: pointer;
}
li.active{
    background: #35075b;
    cursor: pointer;
}
</style>