<template>
  <div
    class="row mx-auto justify-content-center align-items-center text-center"
  >
    <VideoCon
      v-for="index in numOfVid"
      :key="index"
      class="col-lg-2 m-2 videoCon p-0"
      :link="playlist[index - 1].link"
    />
  </div>
</template>

<script>
import VidData from "../database/db.json";
import VideoCon from "@/components/VideoContainer.vue";

export default {
  props: ["limit", "filter"],
  name: "HomeView",
  components: { VideoCon },
  data() {
    return {
      videos: VidData.videos,
      playlist: [],
      numOfVid: 0,
    };
  },
  created() {
    this.shuffle(this.videos);
    if (this.filter === "all" || this.filter == null) {
      this.playlist = this.videos;
    } else {
      this.videos.forEach((video) => {
        video.tags.forEach((tag) => {
          if (tag === this.filter) {
            this.playlist.push(video);
          }
        });
      });
    }

    if (this.limit == null) {
      this.numOfVid = this.playlist.length;
    } else {
      this.numOfVid = this.limit;
    }
  },
  methods: {
    shuffle(array) {
      let currentIndex = array.length,
        randomIndex;

      // While there remain elements to shuffle.
      while (currentIndex != 0) {
        // Pick a remaining element.
        randomIndex = Math.floor(Math.random() * currentIndex);
        currentIndex--;

        // And swap it with the current element.
        [array[currentIndex], array[randomIndex]] = [
          array[randomIndex],
          array[currentIndex],
        ];
      }

      return array;
    },
  },
};
</script>

<style>
</style>