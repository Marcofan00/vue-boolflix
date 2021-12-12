<template>
  <header>
    <div class="search">
      <img src="https://www.cinematographe.it/wp-content/uploads/2018/11/netflix-1.jpg" alt="">
      <h1>BOOLFLIX</h1>
      <div id="cerca">
        <input type="text" placeholder="cerca un film" v-model="testo" @keyup.enter="$emit('search', testo)"/>
        <button @click="$emit('search', testo)">Cerca</button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      testo: "",
    };
  },
  
};
</script>

<style scoped lang="scss">
.search {
  height: 100px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  img{
       max-width: 250px;
      
  }
  h1{
    color: red;
    font-family:Impact,'Arial Narrow Bold', sans-serif
  }
}
</style>
