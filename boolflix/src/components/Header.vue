<template>
    <div class="container">
        <h2>Boolflix</h2>
        <input type="text" placeholder="Cerca qualcosa" v-model="searchText" @keyup="$emit('ricerca', searchText)">
        
    </div>
   
</template>

<script>
export default {
    name: 'Main'
}
</script>

<style lang="scss" scoped>
    .container{
        margin-top: 50px;
        display: flex;
        justify-content: space-around;
            h2{
                color: red;
                font-family: 'Open Sans', sans-serif;
                font-size: 30px;
            }
    }
</style>

