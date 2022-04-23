<template>
  <div>
    <HeaderComp @userSearch="saveSearch"/>
    <MainComp :movies="moviesArray" :shows="showArray" />
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
      showArray: [],
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
    } )
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&language=it-IT&query=${txt}`)
      .then( (res)=>{
      this.showArray = res.data.results
    } )
 
    }
  }
}
</script>

<style lang="scss">
@import "bootstrap/dist/css/bootstrap.min.css";
.flagContainer{
  width: 50px;
  height: 50px;
}

</style>
