<template>
  <div>
    <router-link
      class="style-none"
      style="width: inherit; height: inherit"
      :to="{ name: 'Video', params: { id: vidID } }"
    >
      <div style="width: inherit; height: inherit">
        <img :src="vidThumbnail" style="width: inherit;" />
        <p class="px-1 limit">{{ vidTitle }}</p>
      </div>
    </router-link>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ["link"],
  data() {
    return {
      video: {},
      vidID: " ",
      vidTitle: " ",
      vidThumbnail: "",
    };
  },
  created() {
    axios
      .get(
        "https://www.googleapis.com/youtube/v3/videos?part=snippet&id=" +
          this.link.substring(32) +
          "&fields=items(id,snippet)&key=AIzaSyCPTrVi24wmDt1OF8y50nTVvvJ9d_-Ps18"
      )
      .then((response) => {
        this.video = response.data.items;
        this.vidID = this.video[0].id;
        this.vidTitle = this.video[0].snippet.title;
        this.vidThumbnail = this.video[0].snippet.thumbnails.maxres.url;
      });
  },
};
</script>

<style scoped>
.videoCon {
  width: 350px;
  height: 250px;
  font-size: medium;
}
@media screen and (max-width: 1600px) {
  .videoCon {
    width: 320px;
    height: 225px;
    font-size: small;
  }
}
@media screen and (max-width: 1400px) {
  .videoCon {
    width: 280px;
    height: 200px;
    font-size: small;
  }
}
.thumb{
    object-fit: cover;
}
.style-none {
  text-decoration: none;
  color: #ffffff;
  text-align: left;
}
.limit {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2; /* number of lines to show */
  line-clamp: 2;
  -webkit-box-orient: vertical;
}
</style>