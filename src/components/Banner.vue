<template>
  <header
    class="banner"
    :style="{'background-size':
    'cover',
    'background-image':
    'url(' + this.base_url
    +
    this.movie.backdrop_path + ')'}"
  >
    <div class="banner_contents">
      <h1 class="banner_title">{{movie.name}}</h1>
      <h4 class="banner_rating" v-if="movie.vote_average">
        Viewer Ratings: {{movie.vote_average}}
        <i class="far fa-star"></i>
      </h4>
      <h5 class="banner_description">{{truncate(movie.overview, 399)}}</h5>
      <div class="banner_buttons">
        <button class="banner_button">
          <i class="fas fa-play"></i>Play
        </button>
        <button class="banner_button banner_myList_button">
          <i class="fas fa-plus"></i>My List
        </button>
      </div>
    </div>
    <div class="banner_fadeBottom"></div>
  </header>
</template>

<script>
export default {
  name: "Banner",
  props: ["title", "jsonResponse"],
  data() {
    return {
      movie: null,
      base_url: "https://image.tmdb.org/t/p/original/"
    };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      this.movie = this.jsonResponse.results[
        Math.floor(Math.random() * this.jsonResponse.results.length - 1)
      ];
      return;
    },
    truncate(str, n) {
      return str?.length > n ? str.substr(0, n - 1) + "..." : str;
    }
  },
  computed: {}
};
</script>

<style scoped>
.banner {
  object-fit: contain;
  height: 448px;
  margin-bottom: 10px;
}
.banner_contents {
  margin: 0px 60px;
  padding-top: 140px;
  height: 190px;
}
.banner_title {
  font-size: 3rem;
  padding-bottom: 0.3rem;
  text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
}
.banner_rating {
  padding-left: 13px;
  text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
  font-weight: 600;
}
.banner_description {
  width: 45rem;
  max-width: 500px;
  min-height: 80px;
  padding-top: 1rem;
  color: rgb(211, 211, 211);
  text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.8);
  font-weight: 500;
}
.banner_buttons {
  padding-top: 1rem;
}
.banner_button {
  cursor: pointer;
  transition: 250ms;
  color: #0f0f0f;
  outline: none;
  border: none;
  font-weight: 600;
  font-size: 1.25rem;
  border-radius: 0.2vw;
  padding: 0.5rem 2rem;
  margin-right: 0.8rem;
  background-color: rgb(255, 255, 255);
}
.banner_button:hover {
  background-color: rgb(219, 219, 219);
}
.banner_button.banner_myList_button {
  color: #ffffff;
  background-color: rgba(133, 133, 133, 0.6);
}
button i {
  padding-right: 10px;
}
.banner_button.banner_myList_button:hover {
  background-color: rgba(100, 100, 100, 0.6);
}
.banner_fadeBottom {
  height: 7.4rem;
  background-image: linear-gradient(180deg, transparent, #0f0f0f85, #0f0f0f);
}
</style>
