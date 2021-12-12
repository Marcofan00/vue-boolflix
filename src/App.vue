<template>
  <div id="app">
    <Search @search="movie"
     />
    <Cards :arrayMovie="movies"
    :arraySerie="series"
    />
  </div>
</template>

<script>
import Search from './components/Search.vue'
import Cards from './components/Cards.vue'
import axios from "axios"
export default {
  name: 'App',
  components: {
    Search,
    Cards,
  },
  data(){
    return {
      apiUrl: `https://api.themoviedb.org/3/search/movie?api_key=b39ca0478b010eef31711d4238cdae56`,
      apiUrlSeries: `https://api.themoviedb.org/3/search/tv?api_key=b39ca0478b010eef31711d4238cdae56`,
      query: "&query=",
      language: "&language=it-IT",
      page: "&page=1",
      movies: [],
      series: [],
      inputUtente: ""
    }
  },
 methods: {
    movie(testo) {
      this.inputUtente = testo;
      console.log(this.inputUtente);
      axios
      .get(this.apiUrl + this.language + this.page + this.query + this.inputUtente)
      .then((result) => {
        this.movies = result.data.results;
        console.log(this.movies)
      }),
      this.inputUtente = testo;
      axios
      .get(this.apiUrlSeries + this.language + this.page + this.query + this.inputUtente)
      .then((result) => {
        this.series = result.data.results;
        console.log(this.series);
      })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: black;
}
body{
  background-color: black;
}
</style>
