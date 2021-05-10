<template>
  <main class="content">
      <div class="movie" v-for="movie in movieList" :key="movie.id">
      <Card :info="movie" />
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import Card from '@/components/Card.vue';
export default {
    name: 'Content',
    components: {
        Card,
    },
    data() {
        return {
            apiURL: 'https://api.themoviedb.org/3/search/movie?api_key=1d8038f21df4adea65574db5ad099477&query=ritorno al futuro',
            movieList: [],
        }
    },
    created() {
        this.getMovie();
    },
    methods: {
        getMovie() {
            axios.get(this.apiURL)
                .then(res => {
                    this.movieList = res.data.results;
                })
                .catch(err => {console.log('Error', err);});
        }
    },
}
</script>

<style scoped lang="scss">

.content {
    display: flex;
    flex-direction: column;
    height: calc(100vh - 57px);
    background: #2e2e2e;
    color: #fff;
    padding: 50px 0 0 40px;
}

.movie:not(:first-child) {
    margin-top: 20px;
}

</style>