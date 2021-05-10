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
      apiURL: 'https://api.themoviedb.org/3/search/movie',
      apiURL2: 'https://api.themoviedb.org/3/search/movie',
    }
  },
  methods: {
    updateSearch(text) {
      if(text.length > 0) {
      axios.get(this.apiURL, {
        params: {
          api_key:'1d8038f21df4adea65574db5ad099477',
          query: text,
        }
      }), axios.get(this.apiURL2, {
        params: {
          api_key: '1d8038f21df4adea65574db5ad099477',
          query: text,
        }
      })
      .then(res => {
        this.movieList = res.data.results;
        console.log(this.movieList);
      })
      .catch(err => {console.log('Error', err);});
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
