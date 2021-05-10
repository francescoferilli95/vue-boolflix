<template>
  <div class="card">
      <ul>
          <li>Title: {{info.title == null ? info.name : info.title}}</li>
          <li>Original Title: {{info.original_title == null ? info.original_name : info.original_name}}</li>
         <li v-if="!flags.includes(info.original_language)">Original Language: {{info.original_language}}</li>
         <li v-else>
             <span>Original Language:</span>
             <img class="language" :src="require(`../assets/images/${info.original_language}.png`)" alt="language">
         </li>
          <li>Vote: <i v-for="(n,i) in Math.ceil(info.vote_average /2)" :key="'element' + i" class="fas fa-star"></i>
            <i v-for="(n,ind) in 5 - Math.ceil(info.vote_average /2)" :key="'el' + ind" class="far fa-star"></i></li>
      </ul>
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
}

</style>