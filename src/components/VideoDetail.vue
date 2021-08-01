<template>
    <div v-if="video" class="col-md-8"> <!--skips it till video isn't null-->
      <div class="embed-responsive embed-responsive-16by9"> <!--bs code for responsive embed vid-->
          <iframe class="embed-responsive-item" v-bind:src="videoURL"></iframe> <!--to embed the yt videos in our app-->
      </div>
      <div class="details">
        <h4>{{  video.snippet.title }}</h4> 
        <p>{{ video.snippet.description }}</p>
      </div>
     
    </div>
</template>

<script>
export default {
    name:'VideoDetail',
    props: ['video'],
    computed: {
        videoURL(){
            const videoId = this.video.id.videoId;
            return 'https://www.youtube.com/embed/' + videoId;  //to get the video from yt to play on our app
        }
    }
}

</script>

<style scoped>
.details {
    margin-top: 10px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
}
</style>
