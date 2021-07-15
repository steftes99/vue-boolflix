<template>
    <div class="card">
        <ul>
            <li><strong>Titolo: </strong>{{info.title == null ? info.name : info.title}}</li>
            <li><strong>Titolo originale: </strong>{{info.original_title || info.original_name}}</li>
            <li v-if="flags.includes(info.original_language)">
                <strong>Lingua originale </strong>{{info.original_language}}
                <img :src="
                        require(`../assets/img/${info.original_language}.png`)
                        "
                     :alt="info.original_language">
            
            </li>
            <li v-else><strong>Lingua originale </strong>{{info.original_language}}</li>
            <li><strong>Voto: </strong>{{info.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['info'],
    data(){
        return {
            flags: ['en', 'it']
        }
    }
}
</script>

<style lang="scss" scoped>
    .card{
        width: 200px;
        height: 200px;
        border: 1px solid black;
        display: inline-block;
        margin: 10px;
            ul{
                list-style-type: none;
            }
            img{
                width: 10%;
            }
    }
</style>