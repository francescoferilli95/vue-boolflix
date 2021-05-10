<template>
  <main class="content">
      <div class="movie" v-for="movie in movies" :key="movie.id">
      <Card :info="movie" />
      </div>
  </main>
</template>

<script>
import Card from '@/components/Card.vue';
export default {
    name: 'Content',
    components: {
        Card,
    },
    props: ['movies'],
    methods: {
        getLanguage() {
            this.movies.forEach(el => {
                if(el.original_language === 'it') {
                    el.original_language = '@/assets/images/in.png';
                }
            });
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
    overflow-y: auto;
}

.movie:not(:first-child) {
    margin-top: 20px;
}

</style>