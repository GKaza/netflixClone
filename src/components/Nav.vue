<template>
  <div class="nav" :class="{nav_black: show}">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Netflix_2015_logo.svg/1024px-Netflix_2015_logo.svg.png"
      alt="Netflix Logo"
      class="nav_logo"
    />

    <h5 class="nav_home">Home</h5>
    <h5 class="nav_tab">TV Shows</h5>
    <h5 class="nav_tab">Movies</h5>
    <h5 class="nav_tab">Latest</h5>
    <h5 class="nav_tab">My List</h5>

    <div class="nav_box">
      <div class="account_menu">
        <img
          src="https://pbs.twimg.com/profile_images/1240119990411550720/hBEe3tdn_400x400.png"
          alt="Netflix Avatar"
          class="nav_avatar"
        />
        <i class="fas fa-caret-down less_marg"></i>
      </div>
      <i class="fas fa-bell fa-lg"></i>
      <i class="fas fa-gift fa-lg"></i>
      <i class="fas fa-search fa-lg"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Nav",
  props: [],
  data() {
    return {
      show: false
    };
  },
  created() {},
  mounted: function() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed: function() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleScroll: function() {
      if (window.scrollY > 95) {
        this.show = true;
      } else {
        this.show = false;
      }
    }
  },
  computed: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.nav {
  position: fixed;
  top: 0;
  z-index: 1;
  width: 100%;
  height: 68px;
  padding: 0px 60px;
  display: flex;
  align-items: center;
  transition: 300ms;
}

.nav_black {
  background-color: #0f0f0f;
}

.nav_logo {
  width: 92.5px;
  object-fit: contain;
  margin-right: 25px;
  cursor: pointer;
}
.nav_avatar {
  width: 32px;
  object-fit: contain;
}
.nav_box {
  display: flex;
  flex-direction: row-reverse;
  position: fixed;
  align-items: center;
  right: 60px;
  height: 68px;
}
.account_menu {
  height: 32px;
  display: flex;
  align-items: center;
}
.nav_box .account_menu,
.nav_box i {
  margin-left: 22px;
  cursor: pointer;
}
.nav_box .less_marg {
  margin-left: 5px;
}
.nav_tab {
  margin-left: 20px;
  font-weight: 400;
  cursor: pointer;
  transition: 500ms;
  font-size: 0.9rem;
}
.nav_home {
  margin-left: 20px;
  font-weight: 600;
  cursor: default;
  font-size: 0.9rem;
}
.nav_tab:hover {
  color: rgb(190, 190, 190);
}
</style>
