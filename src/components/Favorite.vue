<script>
export default{
    props:{
        favs:{
            type:Array,
            required:true
        },
        getFromFavs:{
            type:Function,
            required:true
        }
    }
}
</script>
<template>
<h2>Favorites</h2>
<div v-for="(el,i) in favs" :key="i" @click="getFromFavs(i)">
    <span>{{ el.from }}</span>
    <span>{{ el.to }}</span>
</div>
</template>
<style scoped>
h2{
    color: white;
    font-size: medium;
}
div{
    display: flex;
    justify-content: space-between;
    width: 200px;
    transition: all 500ms ease;
    margin: 10px auto;
}
span{
    padding: 10px 15px;
    background: #8c00ff;
    color: white;
}
div:hover{
    opacity: 0.7;
    transform: scale(1.1);
    cursor: pointer;
}
</style>