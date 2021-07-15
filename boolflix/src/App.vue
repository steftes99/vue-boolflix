<template>
  <div id="app">
    <Header @ricerca="ricercaFilm"/>
    <Main :films="films" :campoRicerca="searchText"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      apiUrl: 'https://api.themoviedb.org/3/search/movie?',
      apiKey: 'bc3ca9c37468176456721a114502cca2',
      language: 'it-IT',
      films: [],
      searchText: ''
    }
  },
  methods : {
      ricercaFilm(text){
        this.searchText = text;
          axios
            .get(this.apiUrl,{
              params: {
                  api_key: this.apiKey,
                  language: this.language,
                  query: text
              }
            })
            .then( response => {
              console.log(response.data.results);
              this.films = response.data.results;
            });
        console.log(text);
      }
  }
}
</script>

<style lang="scss">
  @import '@/style/commons.scss'
</style>
