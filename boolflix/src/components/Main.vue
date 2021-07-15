<template>
    <div class="container">
        <h2>Hai cercato: {{campoRicerca}}</h2>
        
        <h4>Film</h4>
        <div class="cards">
            <Card v-for="film in films" :key="film.id" :info="film"/>
        </div>
        <h4>Serie tv</h4>
        <div class="cards">
            <Card v-for="serieTV in tv" :key="serieTV.id" :info="serieTV"/>
        </div>
        
    </div>
</template>

<script>
import Card from '@/components/Card.vue'
export default {
    name: 'Main',
    components: {
        Card,
    },
    props: {
        films: Array,
        tv: Array,
        campoRicerca: String
    }
}
</script>

<style lang="scss" scoped>
    h2{
        margin: 30px;
    }
    .cards{
        display: flex;
        justify-content: flex-start;
        flex-wrap: wrap;
    }
</style>