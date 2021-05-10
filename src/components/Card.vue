<template>
  <div class="card">
      <ul>
          <li>Title: {{info.title}}</li>
          <li v-if="info.title === undefined">Title: {{info.name}}</li>
          <li>Original Title: {{info.original_title}}</li>
          <li v-if="info.original_title === undefined">Original Title: {{info.original_name}}</li>
          <li v-if="info.original_language === 'it'">Original Language: <img class="language" src="@/assets/images/it.png" alt="it"></li>
          <li v-else-if="info.original_language === 'en'">Original Language: <img class="language" src="@/assets/images/en.png" alt="en"></li>
          <li>Vote: {{info.vote_average}}</li>
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