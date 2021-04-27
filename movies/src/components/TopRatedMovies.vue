<template>
    <div>
        <h2>Top Rated Movies</h2>
        <div class="dropdown movies" v-for="(r, i) in resData" :key="`A-${i}`">
        <img :src="'https://image.tmdb.org/t/p/w500' + r.backdrop_path" :alt= "r.title"/>
        <h4 class="m0"> {{ r.title }} <small>({{ r.release_date }})</small></h4>
        <div class="dropdown-content">
            <img :src="'https://image.tmdb.org/t/p/w500' + r.poster_path" :alt= "r.title" width="300" height="200"/>
            <div class="desc">
            <h4 class="m0" v-if="r.original_language != 'en'">{{ r.original_title }}</h4>
            <p class="m0"><small>{{ r.overview }}</small></p>
            </div>
        </div>
        </div>
    </div>
</template>
<script>
import axios from "axios";
export default {
    data () {
        return {
            resData: [],
            more: false,
            tindex: null
        }
    },
    created () {
        axios.get("https://api.themoviedb.org/3/movie/top_rated?api_key=a6f73dcd1cd14b814cd919c333fb33b5&language=en-US&page=1").then(data => {
            console.log('res', data.data.results)
            this.resData = data.data.results;
        });
    }
}
</script>
<style scoped>
.movies {
  width: 30%;
  height: 300px;
  float: left;
  margin: 20px 20px;
}
.m0 {
  margin: 0px;
}
.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 4
  33033000px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
}

.dropdown:hover .dropdown-content {
  display: block;
}

.desc {
  padding: 15px;
  text-align: center;
}
</style>