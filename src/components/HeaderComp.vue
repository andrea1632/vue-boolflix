<template>
    <div class="d-flex justify-content-between bg-dark p-3">
        <h1 class="text-uppercase text-danger">boolflix</h1>
        <input @keyup.enter="$emit('userSearch', textInput)" type="text" v-model="textInput" class="input-group-text">
    </div>
</template>

<script>
export default {
    name: 'HeaderComp',
    data(){
        return{
            textInput : '',
        }
    },
}
</script>

<style scoped>
    
</style>