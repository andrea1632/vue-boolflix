<template>
    <div class="bg-secondary containerCustom">
        <FilmComp :films="movies" />
        <ShowComp :show="shows" />
    </div>
</template>

<script>
import ShowComp from './ShowComp.vue'
import FilmComp from './FilmComp.vue'
export default {
    name: 'MainComp',
    components:{
        FilmComp,
        ShowComp,
    },
    props: {
        movies: Array,
        shows: Array,
    }
}
</script>

<style scoped>
    .containerCustom{
        min-height: calc(100vh - 88px);
    }
</style>