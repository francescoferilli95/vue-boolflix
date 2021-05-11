<template>
  <header class="header">
      <div class="logo">
      <a href="/"><img src="@/assets/images/boolflix.png" alt="logo app"></a>
      </div>
      <div class="search">
            <i class="fa fa-search"></i>
            <input class="text" type="text" placeholder="Search Movies/Series" v-model.trim="searchText">
            <button type="button" @click="$emit('searchingText', searchText)" class="btn">Search</button>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            searchText: '',
        }
    },
}
</script>

<style scoped lang="scss">

.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #000;
    color: red;
    padding: 10px;
}

.logo img {
    width: 50%;
}

.search i {
    margin-right: 10px;
    cursor: pointer;
}

.btn {
    margin-left: 10px;
    padding: 5px;
    border-radius: 5px;
    border: none;
    outline: none;
    text-transform: uppercase;
    background: red;
    color: #fff;
    transition: scale .3s;
    &:hover {
        transform: scale(1.2);
    }
}

.text {
    padding: 5px;
    border-radius: 5px;
    border: none;
    outline: none;
    background: rgba(255,255,255, .4);
    transition: background .3s;
    &:hover,
    &:focus {
        background: #fff;
    }
}

</style>