<template>
  <div class="container">
    <SearchBar @termChange="onTermChange" />
    <div class="row main-content">
      <div style="display: flex">
        <VideoDetail :key="etag" :video="selectedVideo" />
        <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
      </div>
      <PopularVideoList :popularVideos="popularVideos"></PopularVideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import PopularVideoList from "./components/PopularVideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";
const API_KEY = ""; // INSERT YOUR YOUTUBE API KEY HERE
export default {
  mounted() {
    this.onLoadPage();
  },
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
    PopularVideoList,
  },
  data() {
    return {
      videos: [],
      popularVideos: [],
      selectedVideo: null,
    };
  },
  methods: {
    onTermChange(searchTerm) {
      document.getElementById("popular-videos").style.display = "none";
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
        })
        .catch((error) => {
          console.error(error);
          // aqui você pode lidar com o erro adequadamente, como exibir uma mensagem de erro na tela
        });
    },
    onLoadPage() {
      axios
        .get("https://www.googleapis.com/youtube/v3/videos", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            chart: "mostPopular",
          },
        })
        .then((response) => {
          this.popularVideos = response.data.items;
        })
        .catch((error) => {
          console.error(error);
          // aqui você pode lidar com o erro adequadamente, como exibir uma mensagem de erro na tela
        });
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
  },
};
</script>
<style>
body {
  background-color: #f9f8f8;
  margin: 0;
}

.container {
  margin: 0;
  width: 100%;
  max-width: none !important;
}

.main-content {
  justify-content: center;
}
</style>
