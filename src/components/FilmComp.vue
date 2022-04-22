<template>
    <div class="container">
        <div class="row">
            <div class="col-3 cardBoolfix" v-for="elm, index in films" :key="index">
                <div>Titolo:{{elm.title}}</div>
                <div>Titolo originale: {{elm.original_title}}</div>
                <div>Voto: {{elm.vote_average}}</div>
                <div>Overview: {{elm.overview}}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FilmComp',
    props: {
        films: Array,
    }
}
</script>

<style scoped>

</style>