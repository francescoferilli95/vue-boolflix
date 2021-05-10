<template>
  <div id="app">
  <header>
    <Header />
    </header>  
  <main>
    <Content />
  </main>

  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Content from '@/components/Content.vue';

export default {
  name: 'App',
  components: {
    Header,
    Content,
  }
}
</script>

<style lang="scss">

@import '~@fontsource/open-sans/index.css';
@import '~@fontsource/open-sans/700.css';

@import '@/styles/general.scss'; 
</style>
