<template>
    <div>
        <FilmComp :films="movies" />
    </div>
</template>

<script>
import FilmComp from './FilmComp.vue'
export default {
    name: 'MainComp',
    components:{
        FilmComp,
    },
    props: {
        movies: Array,
    }
}
</script>

<style scoped>

</style>