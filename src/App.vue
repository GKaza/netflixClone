<template>
  <div id="app">
    <Nav />
    <Banner title="Banner" :fetchUrl="this.requests.fetchNetflixOriginals" />
    <Row title="NETFLIX Originals" :fetchUrl="this.requests.fetchNetflixOriginals" />
    <Row title="Trending Now" :fetchUrl="this.requests.fetchTrending" />
    <Row title="Top Rated" :fetchUrl="this.requests.fetchTopRated" />
    <Row title="Action Movies" :fetchUrl="this.requests.fetchActionMovies" />
    <Row title="Comedy Movies" :fetchUrl="this.requests.fetchComedyMovies" />
    <Row title="Thriller Movies" :fetchUrl="this.requests.fetchThrillerMovies" />
    <Row title="Horror Movies" :fetchUrl="this.requests.fetchHorrorMovies" />
    <Row title="Animation Movies" :fetchUrl="this.requests.fetchAnimationMovies" />
  </div>
</template>

<script>
import Row from "./components/Row.vue";
import Banner from "./components/Banner.vue";
import Nav from "./components/Nav.vue";

export default {
  name: "App",
  components: {
    Row,
    Banner,
    Nav
  },
  data() {
    return {
      API_KEY: "7b9b3529eaf822da162fcbbf88be2abe",
      requests: null
    };
  },
  methods: {
    setRequests() {
      this.requests = {
        fetchTrending: `/trending/all/week?api_key=${this.API_KEY}&language=en-US`,
        fetchNetflixOriginals: `/discover/tv?api_key=${this.API_KEY}&with_networks=213`,
        fetchTopRated: `/movie/top_rated?api_key=${this.API_KEY}&language=en-US`,
        fetchActionMovies: `/discover/movie?api_key=${this.API_KEY}&with_genres=28`,
        fetchComedyMovies: `/discover/movie?api_key=${this.API_KEY}&with_genres=35`,
        fetchHorrorMovies: `/discover/movie?api_key=${this.API_KEY}&with_genres=27`,
        fetchThrillerMovies: `/discover/movie?api_key=${this.API_KEY}&with_genres=53`,
        fetchAnimationMovies: `/discover/movie?api_key=${this.API_KEY}&with_genres=16`
      };
    }
  },
  created: function() {
    this.setRequests();
  }
};
</script>

<style>
* {
  margin: 0px;
}
body {
  font-family: "Open Sans", sans-serif;
  color: #eeeeee;
  background-color: #0f0f0f;
}
</style>
