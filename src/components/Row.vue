<template>
  <div class="row">
    <h3 class="row_title">{{title}}</h3>
    <div class="row_posters">
      <div class="space"></div>
      <img
        v-for="movie in movies"
        :key="movie.id"
        :src="base_url + movie.backdrop_path"
        :alt="movie.name"
        class="row_poster"
      />
    </div>
  </div>
</template>

<script>
import axios from "../axios";
export default {
  name: "Row",
  props: ["title", "fetchUrl"],
  data() {
    return {
      movies: null,
      base_url: "https://image.tmdb.org/t/p/original/"
    };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const request = await axios.get(this.fetchUrl);
      this.movies = request.data.results;
      return request;
    }
  },
  computed: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.row {
  margin: 0px 60px;
}
.row_title {
  line-height: 0px;
  font-size: 1.3rem;
  font-weight: 600;
}

.row_posters {
  display: flex;
  align-items: center;
  overflow-y: hidden;
  overflow-x: scroll;
  min-height: 215px;
}

.row_posters::-webkit-scrollbar {
  display: none;
}

.row_poster {
  object-fit: contain;
  width: 100%;
  max-height: 126px;
  margin: 0 1px;
  cursor: pointer;
  transition: 500ms;
}

.row_poster:hover {
  max-height: 187px;
}

/* .test {
  color: transparent;
  background: #ffffff86;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  background-clip: text;
  text-shadow: 0px 3px 3px rgba(122, 122, 122, 0.39);
  font-family: 'Permanent Marker', cursive;
} */
</style>
