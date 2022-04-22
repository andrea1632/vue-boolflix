<template>
  <div>
    <HeaderComp @userSearch="saveSearch" />
    <MainComp/>
  </div>
</template>

<script>
//import axios from 'axios';
import "bootstrap"
import HeaderComp from './components/HeaderComp.vue'
import MainComp from './components/MainComp.vue'
export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp,
  },
  data(){
    return{
      moviesArray: [],
      apiKey: "e2f2427f18131144ee68125bfac38779",
      inputSearch: '',
    }
  },
  created(){

  },
  methods:{
    saveSearch(txt){
      this.inputSearch = txt
      console.log(this.inputSearch)
    }
  }
}
</script>

<style lang="scss">
@import "bootstrap/dist/css/bootstrap.min.css";

</style>
