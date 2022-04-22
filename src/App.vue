<template>
  <div>
    <HeaderComp @userSearch="saveSearch" />
    <MainComp :movies="moviesArray" />
  </div>
</template>

<script>
import axios from 'axios';
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
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&language=it-IT&query=${txt}`)
      .then( (res)=>{
      this.moviesArray = res.data.results
      console.log(this.moviesArray)
    } )
 
    }
  }
}
</script>

<style lang="scss">
@import "bootstrap/dist/css/bootstrap.min.css";

</style>
