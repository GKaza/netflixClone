<template>
  <div class="nav" :class="{nav_black: show}">
    <img
      src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/08/Netflix_2015_logo.svg/1024px-Netflix_2015_logo.svg.png"
      alt="Netflix Logo"
      class="nav_logo"
    />

    <div class="nav_menu">
      <div class="toggle_button">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </div>
      <div class="nav_tabs">
        <h5 class="nav_tab nav_home">Home</h5>
        <h5 class="nav_tab">TV Shows</h5>
        <h5 class="nav_tab">Movies</h5>
        <h5 class="nav_tab">Latest</h5>
        <h5 class="nav_tab">My List</h5>
      </div>
    </div>

    <div class="nav_box">
      <div class="account_menu">
        <img
          src="https://pbs.twimg.com/profile_images/1240119990411550720/hBEe3tdn_400x400.png"
          alt="Netflix Avatar"
          class="nav_avatar"
        />
        <i class="fas fa-caret-down less_marg"></i>
        <div class="dropdown_content">
          <div class="menu_item">
            <img
              src="https://mir-s3-cdn-cf.behance.net/project_modules/disp/64623a33850498.56ba69ac2a6f7.png"
              alt="Netflix Avatar"
              class="nav_avatar"
            />
            <p>Other Profile</p>
          </div>
          <div class="menu_item">
            <p>Manage Profiles</p>
          </div>
          <div class="menu_item">
            <p>Account</p>
          </div>
          <div class="menu_item">
            <p>Help Center</p>
          </div>
          <div class="menu_item">
            <p>Sign out of Netflix</p>
          </div>
        </div>
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
.nav_menu {
  height: 68px;
  display: flex;
  align-items: center;
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
  margin-left: 25px;
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
  font-weight: 600;
}
.nav_tab:hover {
  color: rgb(190, 190, 190);
}
.dropdown_content {
  padding-top: 18px;
  position: absolute;
  right: 0px;
  top: 50px;
  cursor: default;
  min-width: 180px;
  display: block;
  opacity: 0;
  visibility: hidden;
  transform: translateY(20%);
  transition: all 500ms;
}
.dropdown_content .menu_item {
  float: none;
  background-color: #0f0f0f;
  padding: 8px;
  display: flex;
  align-items: center;
  text-align: left;
  cursor: pointer;
}
.menu_item img {
  margin-right: 8px;
}
.menu_item p {
  font-weight: 300;
  font-size: 0.8rem;
}
.menu_item:hover p {
  text-decoration: underline;
}
.account_menu:hover .dropdown_content {
  opacity: 1;
  visibility: visible;
  transform: translateY(0%);
}
.nav_tabs {
  height: 68px;
  display: flex;
  align-items: center;
}

.toggle_button {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 18px;
  cursor: pointer;
}

.toggle_button .bar {
  height: 3px;
  width: 100%;
  background-color: #ffffff;
  border-radius: 10px;
}

@media (max-width: 780px) {
  .nav {
    padding: 0px 20px;
  }
  .toggle_button {
    display: flex;
  }
  .nav_tabs {
    padding-top: 18px;
    min-width: 180px;
    display: block;
    opacity: 0;
    visibility: hidden;
    transform: translateY(20%);
    transition: all 500ms;
    position: absolute;
    top: 50px;
    left: -10px;
  }

  .nav_menu .nav_tab {
    float: none;
    background-color: #0f0f0f;
    padding: 8px;
    display: flex;
    align-items: center;
    text-align: left;
    cursor: pointer;
  }
  .nav_tab:hover {
    text-decoration: underline;
  }

  .nav_menu:hover .nav_tabs {
    opacity: 1;
    visibility: visible;
    transform: translateY(0%);
  }
  .nav_menu:hover .bar {
    background-color: rgb(211, 211, 211);
  }
  .nav_box i {
    display: none;
  }
  .nav_box {
    right: 20px;
  }
  .nav_logo {
    margin-right: 20px;
  }
}
</style>
