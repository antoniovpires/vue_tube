<template>
  <ul id="popular-videos" class="list-group col-md-4">
    <VideoListItem
      v-for="video in popularVideos"
      class="VideoListItem"
      :key="video.etag"
      :video="video"
      @videoSelect="onVideoSelect"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue";
export default {
  name: "PopularVideoList",
  components: {
    VideoListItem,
  },
  props: {
    popularVideos: Array,
  },
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    },
  },
};
</script>

<style>
.VideoListItem {
  background-color: #f9f8f8;
}

.list-group {
  flex-direction: row;
  width: 100%;
  flex-wrap: wrap;
}

.list-group li {
  width: 100%;
}
</style>
