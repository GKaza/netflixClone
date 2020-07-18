<template>
  <div id="app">
    <Nav />
    <Banner title="Banner" :jsonResponse="this.requests.fetchNetflixOriginals" />
    <Row title="NETFLIX Originals" id="0" :jsonResponse="this.requests.fetchNetflixOriginals" />
    <Row title="Trending Now" id="1" :jsonResponse="this.requests.fetchTrending" />
    <Row title="Top Rated" id="2" :jsonResponse="this.requests.fetchTopRated" />
    <Row title="Action Movies" id="3" :jsonResponse="this.requests.fetchActionMovies" />
    <Row title="Comedy Movies" id="4" :jsonResponse="this.requests.fetchComedyMovies" />
    <Row title="Thriller Movies" id="5" :jsonResponse="this.requests.fetchThrillerMovies" />
    <Row title="Horror Movies" id="6" :jsonResponse="this.requests.fetchHorrorMovies" />
    <Row title="Animation Movies" id="7" :jsonResponse="this.requests.fetchAnimationMovies" />
  </div>
</template>

<script>
import Row from "./components/Row.vue";
import Banner from "./components/Banner.vue";
import Nav from "./components/Nav.vue";
import action from "./assets/jsonResponses/action.json";
import animation from "./assets/jsonResponses/animation.json";
import comedy from "./assets/jsonResponses/comedy.json";
import horror from "./assets/jsonResponses/horror.json";
import netflix from "./assets/jsonResponses/netflix.json";
import thriller from "./assets/jsonResponses/thriller.json";
import topRated from "./assets/jsonResponses/topRated.json";
import trending from "./assets/jsonResponses/trending.json";

export default {
  name: "App",
  components: {
    Row,
    Banner,
    Nav
  },
  data() {
    return {
      requests: {
        fetchTrending: trending,
        fetchNetflixOriginals: netflix,
        fetchTopRated: topRated,
        fetchActionMovies: action,
        fetchComedyMovies: comedy,
        fetchHorrorMovies: horror,
        fetchThrillerMovies: thriller,
        fetchAnimationMovies: animation
      }
    };
  },
  methods: {},
  created: function() {}
};
</script>

<style>
* {
  margin: 0px;
}
body {
  font-family: "Poppins", sans-serif;
  color: #eeeeee;
  background-color: #0f0f0f;
}
</style>
