<template>
  <div class="row">
    <h3 class="row_title">{{title}}</h3>
    <div class="row_posters" @scroll="getVal()">
      <div class="wrap" v-for="movie in movies" :key="movie.id">
        <img :src="base_url + movie.backdrop_path" :alt="movie.name" class="row_poster" />
        <h5 class="poster_title" v-if="movie.name">{{movie.name}}</h5>
        <h5 class="poster_title" v-if="movie.title">{{movie.title}}</h5>
        <div class="poster_info">
          <h4 v-if="movie.name">{{movie.name}}</h4>
          <h4 v-if="movie.title">{{movie.title}}</h4>
          <p>{{truncate(movie.overview,150)}}</p>
        </div>
      </div>
      <div class="space"></div>
      <div class="left_arrow scroll_button" v-if="left_value" @click="scrollLeft()">
        <i class="fas fa-angle-left fa-lg"></i>
      </div>
      <div class="right_arrow scroll_button" v-if="right_value > 2" @click="scrollRight()">
        <i class="fas fa-angle-right fa-lg"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Row",
  props: ["title", "jsonResponse", "id"],
  data() {
    return {
      movies: null,
      base_url: "https://image.tmdb.org/t/p/original/",
      left_value: 0,
      right_value: 3
    };
  },
  created: function() {
    this.fetchData();
  },
  mounted: function() {},
  methods: {
    async fetchData() {
      this.movies = this.jsonResponse.results;
      return;
    },
    truncate(str, n) {
      return str?.length > n ? str.substr(0, n - 1) + "..." : str;
    },
    scrollLeft() {
      let x = document.getElementsByClassName("row_posters")[this.id];
      let step = window.outerWidth / 2;
      x.scrollLeft -= step;
    },
    scrollRight() {
      let x = document.getElementsByClassName("row_posters")[this.id];
      let step = window.outerWidth / 2;
      x.scrollLeft += step;
    },
    getVal() {
      setTimeout(() => {
        let x = document.getElementsByClassName("row_posters")[this.id];
        this.left_value = x.scrollLeft;
        this.right_value = x.scrollWidth - (x.scrollLeft + x.clientWidth) + 1;
        console.log(this.right_value);
      }, 550);
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
  transition: 500ms;
  scroll-behavior: smooth;
}

.row_posters::-webkit-scrollbar {
  display: none;
}

.row_poster {
  object-fit: contain;
  height: 100%;
}

.wrap {
  display: inline-block;
  position: relative;
  height: 100px;
  width: fit-content;
  margin: 0 1px;
  cursor: pointer;
  transition: height 500ms;
}

.wrap:hover {
  height: 187px;
}

.poster_title {
  font-family: "Cinzel", serif;
  position: absolute;
  left: 20px;
  bottom: 20px;
  color: #f0f0f0;
  text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  opacity: 1;
  transition: opacity 2000ms 1000ms;
}
.wrap:hover .poster_title {
  opacity: 0;
  transition: opacity 100ms;
}

.poster_info {
  position: absolute;
  left: 5px;
  bottom: 50px;
  font-weight: 300;
  font-size: 0.75rem;
  width: 250px;
  text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.8);
  opacity: 0;
  transition: opacity 100ms;
}
.wrap:hover .poster_info {
  opacity: 1;
  transition: opacity 2000ms;
}
.poster_info p {
  padding-top: 5px;
}
.scroll_button {
  position: absolute;
  height: 187px;
  width: 43px;
  background-color: #0f0f0f4b;
  display: flex;
  align-items: center;
  justify-content: space-around;
  cursor: pointer;
}
.right_arrow {
  right: 60px;
  opacity: 0;
  visibility: hidden;
  transform: translateX(20%);
  transition: all 500ms;
}
.left_arrow {
  left: 60px;
  opacity: 0;
  visibility: hidden;
  transform: translateX(-20%);
  transition: all 500ms;
}
.row_posters:hover .right_arrow {
  opacity: 1;
  visibility: visible;
  transform: translateX(0%);
}
.row_posters:hover .left_arrow {
  opacity: 1;
  visibility: visible;
  transform: translateX(0%);
}
.space {
  min-width: 155px;
  height: 126px;
}

@media (max-width: 780px) {
  .row {
    margin: 0px 0px;
  }
  .scroll_button {
    display: none;
  }
  .space {
    display: none;
  }
  .row_title {
    margin-left: 20px;
  }
}
</style>
