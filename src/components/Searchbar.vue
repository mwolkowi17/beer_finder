<template>
<div>
    
    <input placeholder="find beer">
    <button><b>Find</b></button>
</div>
</template>

<script>
export default{
    name: "Searchbar",
    data(){
        return{
            info: "Searchbar"
        }
    }
}
</script>

<style scoped>
div{
    height: 80px;
    background-color: darkgreen
}
input{
    margin-top: 29px;
    height: 40px;
    font-size: 20px;
}
button{
    height: 46px;
    width: 140px;
    color: black;
    
    margin-bottom: 20px;
    bottom: 3px;
    position: relative;
    background-color: red;
}
</style>>

