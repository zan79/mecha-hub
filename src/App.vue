<template>
  <nav
    class="
      dark-bg
      d-flex
      justify-content-between
      align-items-center
      fixed-top
      px-2
    "
  >
    <div class="sbar d-flex justify-content-start" style="width: 250px">
      <span @click="toogle()" class="m-2 d-flex align-items-center"
        ><img src="https://img.icons8.com/ios-glyphs/30/FFFFFF/menu--v1.png"
      /></span>
      <router-link to="/home/all"
        ><img src="./assets/mechahub-logo.png" alt="" style="width: 180px"
      /></router-link>
    </div>

    <!-- <div class="searchbar d-flex justify-content-center" style="width: 700px">
      <input
        class="form-control mx-1"
        type="search"
        placeholder="Search"
        aria-label="Search"
        style="width: 600px"
        v-model="searchInput"
      />
      <button class="btn btn-outline-success" @click="search()">S</button>
    </div> -->

    <div class="others d-flex justify-content-end" style="width: 250px">
      <img
        src="./assets/lsp-logo.png"
        alt=""
        class="mx-2"
        style="width: 30px"
      />
      <img
        src="./assets/soncraft-logo.png"
        alt=""
        class="mx-2"
        style="width: 30px"
      />
    </div>
  </nav>

  <div class="content d-flex">
    <div class="" style="padding-top: 60px">
      <Sidebar ref="side" class="" />
    </div>
    <div class="" style="overflow-y: auto; height: 100vh; padding-top: 60px">
      <router-view :key="$route.path" />
    </div>
  </div>
</template>

<script>
import Sidebar from "@/components/SidebarMenu.vue";

export default {
  components: { Sidebar },
  data() {
    return {
      searchInput: "",
    };
  },
  methods: {
    toogle() {
      this.$refs.side.toggle();
    },
    search() {
      this.$router.push({ name: "Search", params: { keyword: "vidID" } });
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #181818;
}

nav a {
  font-weight: bold;
  color: #ffffff;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: #ff6600;
}
nav {
  height: 60px;
}
.content {
  height: 100vh;
}
.darker-bg {
  background-color: #181818;
}
.dark-bg {
  background-color: #202020;
}
</style>
