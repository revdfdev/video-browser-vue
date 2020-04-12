<template>
  <div class="container">
    <SearchBar v-on:termChange="onTermChange"></SearchBar>
     <div>
      <VideoDetails v-bind:video="selectedVideo" />
      <VideoList v-bind:videos="videos" v-on:videoSelect="onVideoSelected" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetails from './components/VideoDetails';
const API_KEY = `${process.env.VUE_APP_GOOGLE_VIDEO}`;

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetails
  },
  data: function () {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    async onTermChange(searchTerm) {
      try {
        const response = await axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      });
      this.videos = response.data.items;

      } catch (e) {
        console.log("Error", e.message)
      }
    },
    onVideoSelected(video) {
      this.selectedVideo = video;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
