<template>
  <div id="app">
    <Header @ricerca="ricercaFilm"/>
    <Main :films="films" :tv="tv" :campoRicerca="searchText"/>
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
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
      apiTvUrl: 'https://api.themoviedb.org/3/search/tv',
      apiKey: 'bc3ca9c37468176456721a114502cca2',
      language: 'it-IT',
      films: [],
      tv: [],
      searchText: ''
    }
  },
  methods:{
      ricercaFilm(text) {
        this.searchText = text;

        const request = {
            params: {
              api_key: this.apiKey,
              language: this.language,
              query: text
            }
        };

        axios
            .all([
                axios.get(this.apiUrl, request),
                axios.get(this.apiTvUrl, request)
            ])
            .then(axios.spread( ( responseMovies, responseTv) => {
                this.films = responseMovies.data.results;
                this.tv = responseTv.data.results;
            }));
      }
  }
}
</script>

<style lang="scss">
  @import '@/style/commons.scss'
</style>
