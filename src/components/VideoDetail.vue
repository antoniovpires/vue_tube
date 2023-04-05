<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9" style="height: 70%">
      <iframe
        class="embed-responsive-item"
        style="width: 100%; height: 100%"
        :src="videoUrl"
      />
    </div>
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.video.id.videoId}`;
    },
  },
};
</script>
<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: #f9f8f8;
}
</style>
