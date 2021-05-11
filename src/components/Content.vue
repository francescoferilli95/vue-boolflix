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
}
</script>

<style scoped lang="scss">

.content {
    display: flex;
    flex-wrap: wrap;
    height: calc(100vh - 57px);
    background: #2e2e2e;
    color: #fff;
    padding: 50px 0 0 40px;
    overflow-y: auto;
}

.movie {
    width: calc(100% / 5);
    height: 500px;
    margin: 20px 0;
}

</style>