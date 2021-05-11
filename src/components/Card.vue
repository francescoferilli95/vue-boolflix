<template>
  <div class="card">
      <div class="poster">
          <div v-if="info.backdrop_path == null"><img class="no-poster" src="@/assets/images/no-poster.png" alt="no poster"></div>
        <div v-else><img :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`" alt="poster"></div>
      </div>
      <div class="description">
          <h2>Title: {{info.title == null ? info.name : info.title}}</h2>
          <h2>Original Title: {{info.original_title == null ? info.original_name : info.title}}</h2>
          <p v-if="!flags.includes(info.original_language)">Original Language: {{info.original_language}}></p>
          <p v-else><span>Original Language:</span><img class="language" :src="require(`../assets/images/${info.original_language}.png`)" alt="language"></p>
          <p>Vote: <i v-for="(n,i) in Math.ceil(info.vote_average /2)" :key="'element' + i" class="fas fa-star star"></i>
            <i v-for="(n,ind) in 5 - Math.ceil(info.vote_average /2)" :key="'el' + ind" class="far fa-star"></i></p>
            <p>Overview: {{info.overview}}</p>
      </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['info'],
    data() {
        return {
            flags: ['en', 'it'],
        }
    }
}
</script>

<style scoped lang="scss">

.language {
    width: 20px;
    height: 10px;
    margin-left: 10px;
}

.card {
    position: relative;
    width: 100%;
    height: 100%;
    &:hover .description {
        display: flex;
    }
}

.poster {
    cursor: pointer;
}

.no-poster {
    width: 342px;
    height: 500px;
}

.description {
    display: none;
    flex-direction: column;
    justify-content: center;
    position: absolute;
    top: 0;
    left: 0;
    padding: 20px;
    width: 342px;
    height: 100%;
    background: rgba(0,0,0, .7);
    color: #fff;
    overflow: auto;
    cursor: pointer;
    transition: display .3s;
}

h2 {
    margin-bottom: 10px;
}

p {
    margin-bottom: 10px;
}

.star {
    color: yellow;
}

</style>