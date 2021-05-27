<template>
  <div id="app">
    <Head @startSearch="startSearch"/>

    <h1 v-if="results.movie.length === 0 && results.tv.length === 0">Nessun risultato trovato</h1>
    <Main v-if="results.movie.length > 0"  type='movie' :list="results.movie" />
    <Main v-if="results.tv.length > 0" type='tv' :list="results.tv"/>
  </div>
</template>

<script>
import axios from 'axios';
import Head from './components/Head'
import Main from './components/Main'

export default {
  name: 'App',
  components: {
    Head,
    Main,
  },
  
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiKey: 'be73bf1bdc8180a6c063884c49e5e5f2',
      results:{
        'movie':[],
        'tv':[]
      }
    }
  },

  methods:{
    startSearch(obj){
      this.resetResults();
      if(obj.type === 'all'){
        this.getAPI(obj.text, 'movie');
        this.getAPI(obj.text, 'tv');
      }else{
        this.getAPI(obj.text, obj.type);
      }
    },

    resetResults(){
      this.results.movie = [];
      this.results.tv = [];
    },

    getAPI(query, type){
      if(query !== ''){
        axios.get(this.apiUrl+type,{
            params:{
              api_key: this.apiKey,
              query: query,
              language: 'it-IT'
            }
          })
          .then(res => {
            this.results[type] = res.data.results;
            console.log('MOVIE',this.results.movie);
            console.log('TV', this.results.tv);
          })
          .catch(err => {
            console.log(err);
          })
      }
    }
  },
  created(){
  }
}
</script>

<style lang="scss">

</style>
