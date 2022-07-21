<template>
  <div class="bg-black">
    <iframe
      class="player"
      :src="src"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
    ></iframe>
  </div>
  <div class="py-2 px-5">
    <p class="title px-5 m-0 p-0">{{ title }}</p>
  </div>
  <hr class="m-0 bg-light" />
  <VideoGrid class="pt-3" :limit="5" />
</template>

<script>
import axios from "axios";
import { useRoute } from "vue-router";
import VideoGrid from "@/components/VideoGallery.vue";

export default {
  name: "PlayerView",
  components: { VideoGrid },
  data() {
    return {
      video: {},
      src: " ",
      title: " ",
    };
  },
  mounted() {
    const route = useRoute();
    const id = route.params.id;
    this.src =
      "https://www.youtube.com/embed/" + id + "?rel=0?&autoplay=1";

    axios
      .get(
        "https://www.googleapis.com/youtube/v3/videos?part=snippet&id=" +
          id +
          "&fields=items(id,snippet)&key=AIzaSyCPTrVi24wmDt1OF8y50nTVvvJ9d_-Ps18"
      )
      .then((response) => {
        this.video = response.data.items;
        this.title = this.video[0].snippet.title;
      });
  },
};
</script>

<style scoped>
.title {
  color: #ffffff;
  font-size: 2em;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
.player {
  width: 1280px;
  height: 720px;
}
@media screen and (max-width: 1600px) {
  .player {
    width: 1120px;
    height: 630px;
  }
  .title {
    font-size: 1.5em;
  }
}
@media screen and (max-width: 1400px) {
  .player {
    width: 960px;
    height: 540px;
  }
  .title {
    font-size: 1em;
  }
}
</style>