<template>
  <div>
    <button @click="show()">sdhladh</button>
    <h1>No results found</h1>
    <h2 v-for="res in searchResult" :key="res">
      {{ res.title }}
    </h2>
  </div>
</template>

<script>
// @ is an alias to /src
import { useRoute } from "vue-router";
import axios from "axios";
import VidData from "../database/db.json";

export default {
  name: "SearchView",
  data() {
    return {
      keyword: "maid",
      loaded: false,
      searchResult: [
        {
          id: "a",
          title: "Let's Build Lala Satalin Deviluke Maid Ver.",
        },
        {
          id: "1",
          title: "dawn hdiw d DWA",
        },
        {
          id: "1",
          title: "dawn CAT",
        },
      ],
      videos: VidData.videos,
    };
  },
  async created() {
    const route = useRoute();
    this.keyword = route.params.keyword;

    this.videos.forEach((element) => {
      axios
        .get(
          "https://www.googleapis.com/youtube/v3/videos?part=snippet&id=" +
            element.link.substring(32) +
            "&fields=items(id,snippet)&key=AIzaSyCPTrVi24wmDt1OF8y50nTVvvJ9d_-Ps18"
        )
        .then((response) => {
          this.video = response.data.items;
          this.searchResult.push({
            id: this.video[0].id,
            title: this.video[0].snippet.title,
          });
        });
    });

    setTimeout(() => {
      this.getMatchingResults('Maid')
      this.loaded = true;
    }, 500);
  },
  methods: {
    getMatchingResults(input) {
      this.searchResult = this.searchResult.filter((d) =>
        input
          .split(" ")
          .every((v) => d.title.toLowerCase().includes(v.toLowerCase()))
      );
    },
    show() {
      console.log(this.getMatchingResults("Maid"));
    },
  },
};
</script>

<style scoped>
</style>
