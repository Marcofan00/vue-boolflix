<template>
  <main>
    <div class="contain-cards">
      <div class="cards" v-for="(films, i) in arrayMovie" :key="i">
        <img :src="getPoster(films)" alt="" class="poster" />
        <div class="contain_poster">
          <h1>{{ films.title }}</h1>
          <h2>{{ films.original_title }}</h2>
          <div class="flag">
            <img
              v-if="getFlags(films) !== `notfound`"
              :src="getFlags(films)"
              alt=""
              class="bandiere"/>
            <p v-if="films.original_language === `notfound`">
              {{ films.original_language }}
            </p>
          </div>
        </div>
      </div>

      <div class="cards" v-for="(series, i) in arraySerie" :key="i">
        <img :src="getPoster(series)" alt="" class="poster" />
        <div class="contain_poster">
        <h1>{{ series.name }}</h1>
        <h2>{{ series.original_title }}</h2>
        <div class="flag">
          <img
            v-if="getFlags(series) !== `notfound`"
            :src="getFlags(series)"
            alt=""
            class="bandiere"
          />
          <p v-if="series.original_language === `notfound`">
            {{ series.original_original_language }}
          </p>
        </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Cards",
  props: {
    arrayMovie: Array,
    arraySerie: Array,
  },
  methods: {
    getFlags(flag) {
      if (flag.original_language === `en`) {
        return `https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/280px-Flag_of_the_United_Kingdom_%283-5%29.svg.png`;
      } else if (flag.original_language === `it`) {
        return `https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Flag_of_Italy_%28Pantone%2C_2003%E2%80%932006%29.svg/220px-Flag_of_Italy_%28Pantone%2C_2003%E2%80%932006%29.svg.png`;
      } else if (flag.original_language === `es`) {
        return `https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Flag_of_Spain.svg/2000px-Flag_of_Spain.svg.png`;
      } else {
        return `notfound`;
      }
    },
    getPoster(image) {
      if (image.poster_path !== null) {
        return `https://image.tmdb.org/t/p/w342${image.poster_path}`;
      } else
        return `https://logowik.com/content/uploads/images/netflix-n.jpg`;
    },
  },
};
</script>

<style scoped lang="scss">
main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.contain-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  height: 800px;
  width: 80%;
  .cards {
    height: 400px;
    position: relative;
    width: calc(90% / 5);
    background-color: rgb(255, 255, 255);
    margin: 10px;
    .bandiere {
      max-width: 40px;
    }
  }
}
.poster {
  height: 400px;
  max-width: 100%;
  object-fit: cover;
  display: block;
}
.contain_poster{
  height: 100%;
  width: 100%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  opacity: 0;
  background-color: rgba(0, 0, 0, 0.6);
  transition: opacity 0.25s;
  
}
.contain_poster:hover{
  opacity: 1;
}
</style>