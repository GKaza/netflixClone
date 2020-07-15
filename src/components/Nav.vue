<template>
  <div class="nav" :class="{nav_black: show}">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Netflix_2015_logo.svg/1024px-Netflix_2015_logo.svg.png"
      alt="Netflix Logo"
      class="nav_logo"
    />
    <img
      src="https://pbs.twimg.com/profile_images/1240119990411550720/hBEe3tdn_400x400.png"
      alt="Netflix Avatar"
      class="nav_avatar"
    />
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
}
.nav_avatar {
  width: 32px;
  position: fixed;
  right: 60px;
  object-fit: contain;
}
</style>
