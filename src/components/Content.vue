<template>
  <main class="content">
      <Card />
  </main>
</template>

<script>
import Card from '@/components/Card.vue';
export default {
    name: 'Content',
    components: {
        Card,
        
    },
}
</script>

<style scoped lang="scss">

.content {
    display: flex;
    height: calc(100vh - 57px);
    background: #2e2e2e;
    color: #fff;
    padding: 100px 0 0 20px;
}

</style>