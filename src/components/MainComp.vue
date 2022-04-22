<template>
    <div>
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

</style>