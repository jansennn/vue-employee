<template>
    <div>
        <br>
        <br>
        <h1>Welcome</h1>
        <img id="img" v-bind:src="image" >
    </div>
</template>

<script>
export default {
    name: "Home",
    data(){
        return{
            image: "https://img.freepik.com/free-vector/people-putting-puzzle-pieces-together_52683-28610.jpg?size=626&ext=jpg"
        }
    }
}
</script>

<style>
    #img{
        text-align: center;
        margin-left: 33%;
        margin-right: 35%;
        margin-top: 5%;
    }
</style>