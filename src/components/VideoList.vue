<template>
    <ul class="list-group col-md-4">
        <VideoListItem 
        v-for="video in videos" 
        :key="video.etag"
        v-bind:video="video"
        @videoSelect="onVideoSelect"> <!--"video" refers to the above video in videos, videos is the prop passed-->
        </VideoListItem> <!--etag is a unique identifer for youtube so we use that instead of id-->
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem';
  export default {
      name: 'VideoList',
      components: {
          VideoListItem
      },
      props: { // ['videos'] //name of property to receive
          videos: Array
          },

      methods: {
          onVideoSelect(video){
              this.$emit('videoSelect', video);
          }
      }
  };
</script>

<style>

</style>
