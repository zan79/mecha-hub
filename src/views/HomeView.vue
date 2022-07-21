<template>
  <div class="home">
    <VideoGrid class="pt-3" :filter="src" />
  </div>
</template>

<script>
// @ is an alias to /src
import { useRoute } from "vue-router";
import VideoGrid from "@/components/VideoGallery.vue";

export default {
  name: "HomeView",
  components: { VideoGrid },
  data() {
    return {
      src: "",
    };
  },
  created() {
    const route = useRoute();
    this.src = route.params.src;
  },
};
</script>

<style scoped>
</style>
