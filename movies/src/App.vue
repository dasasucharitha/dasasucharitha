<template>
  <HelloWorld msg="Movies"/>
  <button @click="topRated">Top Rated Movies</button>
  <button @click="upcoming">Upcoming Movies</button>
  <TopRatedMovies v-if="mflag == 'top_rated'"/>
  <UpcomingMovies v-if="mflag == 'upcoming'"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TopRatedMovies from './components/TopRatedMovies.vue'
import UpcomingMovies from './components/UpcomingMovies.vue'

export default {
  name: 'App',
  data() {
    return {
      mflag: null,
      tflag: false,
      uflag: false
    }
  },
  components: {
    HelloWorld,
    TopRatedMovies,
    UpcomingMovies
  },
  methods: {
    topRated() {
      this.mflag = 'top_rated'
    },
    upcoming() {
      this.mflag = 'upcoming'
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  padding: 10px;
  margin: 10px;
  background-color: aquamarine;
  border: 1px solid aquamarine;
}
</style>
