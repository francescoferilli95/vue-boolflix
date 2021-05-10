<template>
  <div class="card">
      <ul>
          <li>Title: {{info.title}}</li>
          <li v-if="info.title === undefined">Title: {{info.name}}</li>
          <li>Original Title: {{info.original_title}}</li>
          <li v-if="info.original_title === undefined">Original Title: {{info.original_name}}</li>
          <li v-if="info.original_language === 'it'">Original Language: <img class="language" src="@/assets/images/it.png" alt="it"></li>
          <li v-else-if="info.original_language === 'en'">Original Language: <img class="language" src="@/assets/images/en.png" alt="en"></li>
          <li>Vote: <i v-for="(n,i) in Math.ceil(info.vote_average /2)" :key="'element' + i" class="fas fa-star"></i>
            <i v-for="(n,ind) in 5 - Math.ceil(info.vote_average /2)" :key="'element' + ind" class="far fa-star"></i></li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['info'],
}
</script>

<style scoped lang="scss">

.language {
    width: 20px;
    height: 10px;
}

</style>