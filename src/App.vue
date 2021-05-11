<template>
  <div id="app">
  <header>
    <Header @searchingText="updateSearch"/>
    </header>  
  <main>
    <Content :movies="movieList" />
  </main>

  </div>
</template>

<script>
import axios from 'axios';
import Header from '@/components/Header.vue';
import Content from '@/components/Content.vue';

export default {
  name: 'App',
  components: {
    Header,
    Content,
  },
  data() {
    return {
      movieList: [],
      seriesList: [],
      movieURL: 'https://api.themoviedb.org/3/search/movie',
      seriesURL: 'https://api.themoviedb.org/3/search/tv',
      weekMovieURL: 'https://api.themoviedb.org/3/trending/movie/week',
      weekSeriesURL: 'https://api.themoviedb.org/3/trending/tv/week',
    }
  },
  created() {
    axios.get(this.weekMovieURL, {
      params: {
        api_key: '1d8038f21df4adea65574db5ad099477',
      }
    })
    .then(el => {
      this.movieList = el.data.results;
    })
    .catch(er => {console.log('Error', er);})
  },
  methods: {
    updateSearch(text) {
      if (text.length > 0) {
      axios.get(this.apiURL, {
        params: {
          api_key:'1d8038f21df4adea65574db5ad099477',
          query: text,
        },  
      })
      .then(res => {
        this.movieList = res.data.results;
        console.log(this.movieList);
      })
      .catch(err => {console.log('Error', err)});
    }
      else {
        alert('Please insert at least one letter');
      }
      if (text.length > 0) {
        axios.get(this.apiURL2, {
        params: {
          api_key: '1d8038f21df4adea65574db5ad099477',
          query: text,
        }
      })
      .then(result => {
        this.seriesList = result.data.results;
        console.log(this.movieList);
      })
      .catch(error => {console.log('Error', error);});
      } else {
        alert('Please insert at least one letter');
      }
    }
  },
}
</script>

<style lang="scss">

@import '~@fontsource/open-sans/index.css';
@import '~@fontsource/open-sans/700.css';

@import '@/styles/general.scss'; 
</style>
