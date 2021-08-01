<template>
  <div id="app" class="container">
  <SearchBar @termChange="onTermChange"></SearchBar>
  <div class="row">
  <VideoDetail :video="selectedVideo"></VideoDetail>
  <VideoList @videoSelect="onVideoSelect" v-bind:videos="videos"></VideoList>
  </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';


const API_KEY = 'AIzaSyBguojs4t9nvyfDX8TbTvjfpebKZjszTqw';


export default {
  name: 'app',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data (){
    return { videos: [], selectedVideo:null };
  },
  methods: {
    onVideoSelect(video){
      this.selectedVideo = video;
    },

    onTermChange: function(searchTerm){
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params:{
          key:API_KEY,
          type: 'video',
          part: 'snippet', //we want a small part of information about the videos
          q: searchTerm //q, short for query
        }
      }).then(response => {
        this.videos = response.data.items //data here refers to the data(response) we are getting from youtube 
      });
    }
  }
}
</script>

<style>

</style>
