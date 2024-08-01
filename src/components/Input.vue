<script>
export default{
    props:{
        changeAmount:{
            type:Function,
            required:true,
        },
        convert:{
            type:Function,
            required:true
        },
        favorite:{
            type:Function,
            required:true,
        }
    }
}
</script>

<template>
    <input min="0" type="number" @input="changeAmount($event.target.value)" placeholder="Enter number">
    <br>
    <button @click="convert()">Convert</button>
    <button @click="favorite()" class="fav-b">Favorite</button>
</template>

<style scoped>
input{
    outline: none;
    width: 500px;
    position: relative;
    font-size: 1.2em;
    top: -20px;
    border-radius: 3px;
    border: 0;
    padding: 10px 15px;
    background: #fafafa;
    color: black;
}
button{
    position: relative;
    top: -10px;
    padding: 15px 20px;
    color: white;
    text-transform: uppercase;
    cursor: pointer;
    background: #1a032d;
    border: 0;
    border-radius: 10px;

}
.fav-b{
    margin-left: 20px;
}
</style>