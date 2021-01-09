<template>
  <div id="app">
    <div class="header">
      <form v-on:submit.prevent="showPhoto">
        <label for="name">
          <input placeholder="Search for photo" id="name" v-model="keyword" />
          <i class="fa fa-search"></i>
        </label>
      </form>
    </div>
    <div v-if="loadImage">
      <Home v-if="images.length" :currentImage="images" />
    </div>
    <div v-else>
      <Main />
    </div>
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Main from "./components/Main.vue";
import axios from "axios";
require("dotenv").config();

export default {
  name: "App",
  components: {
    Home,
    Main,
  },

  data: () => ({
    keyword: "",
    images: [],
    loadImage: false,
  }),

  methods: {
    showPhoto: function(query) {
      const accessToken = "A3F7DkBC723hfY2m0QUuB290UqyWu_1WGQpY-KpVBZg";
      axios({
        method: "get",
        url: "https://api.unsplash.com/search/photos?page=1&per_page=8",
        headers: {
          Authorization: `Client-ID ${accessToken}`,
        },
        params: {
          query: this.keyword,
        },
      })
        .then((response) => {
          this.loadImage = true;
          // console.log(response.data.results);
          this.images = response.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
