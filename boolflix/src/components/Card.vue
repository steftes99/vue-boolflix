<template>
    <div class="card">
        <ul>
            <li><strong>Titolo:</strong>{{info.title}}</li>
            <li><strong>Titolo originale:</strong>{{info.original_title}}</li>
            <li><strong>Lingua originale</strong>{{info.original_language}}</li>
            <li><strong>Voto:</strong>{{info.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['info']
}
</script>

<style lang="scss" scoped>
    .card{
        width: 150px;
        height: 200px;
        border: 1px solid black;
        display: inline-block;
        margin: 10px;
            ul{
                list-style-type: none;
            }
    }
</style>