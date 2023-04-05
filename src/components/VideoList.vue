<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="video in videos"
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
  name: "VideoList",
  components: {
    VideoListItem,
  },
  props: {
    videos: Array,
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
</style>
