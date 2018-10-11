
<template>
  <div class="hello">
    <h1>Video Module</h1>
    <p>You can add a title and the url for your video</p>
    <input type="text" id="newVideoTitle" v-model="newVideoTitle" placeholder="Title" /><br>
    <input type="text" id="newVideoUrl" v-model="newVideoUrl" placeholder="url" /><br>
    <span>Example: https://staging.coverr.co/s3/mp4/Snow-motion.mp4</span>
    <br>
    <button v-on:click="addVideo(videos.count)" id="addVideo">Add New Video</button>
    <ul>
        <li v-for="video in videos" :key="video.id" >
            <h3>{{ video.title + " (" + video.id + ")"}}</h3>
             <p>{{ video.url }}</p>
             <button v-on:click="show(video.url)">View</button>
        </li>
    </ul>
    <modal name="test" :width="640" :height="360">
    <!--
      <video id="my-player" class="video-js" controls preload="auto" poster="//vjs.zencdn.net/v/oceans.png" data-setup='{}' v-bind:src=name ></video>
    -->

    
    
    <video controls v-bind:src=name width="640"></video>

  </modal>
  </div>
</template>
<script>
window.videojs = require('video.js');
//import videojs from 'video.js'
export default {
    name: 'VideoModule',
    prop: {
    },
    data() {
        return {
            name: "",
            showModal: true,
            videos: [{
                id: 0,
                title: "Church",
                url: "https://staging.coverr.co/s3/mp4/Chruch.mp4"
            },
            {
                id: 1,
                title: "Road",
                url: "https://staging.coverr.co/s3/mp4/Road-candies.mp4"
            },
            {
                id: 2,
                title: "Las Vegas",
                url: "https://staging.coverr.co/s3/mp4/Not-Eiffel.mp4"
            },
            {
                id: 3,
                title: "Wing",
                url: "https://staging.coverr.co/s3/mp4/New-jumbo.mp4"
            }],
            newVideoId: 4,
            newVideoTitle: '',
            newVideoUrl: '',
            deleted: false
        }
    },
  
    methods: {
        addVideo: function() {
            this.videos.push({id: this.newVideoId++, title: this.newVideoTitle, url: this.newVideoUrl});
        },
        showVideo: function(url) {
           alert(url);
        },
        show(url) {
                
                this.$modal.show('test');
                this.name = url;
                
        },

        hide () {
                this.$modal.hide('test');
        }
    }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
    background: #fff;
    margin: 10px;
    padding: 10px;
    padding-top: 0px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  background: #818CC0;
  padding: 10px;
  margin-bottom: 10px;
  box-shadow: 1px 1px 3px #46484A;
  border-radius: 2px; 
  border-left: 5px solid #5F678D;
  
}
li h3 {
    margin: 0;
    padding: 0;
    color: #DEE4E8;

}
li p {
    margin: 0;
    padding: 0;
    color: #F1F8FD;
    font-size: 12px;

}
button {
    float: right;
    border: 2px solid #A0AFEF;
    border-radius: 2px; 
    margin: -32px 0px;
    background: #5F678D;
    color: #d8d8d8;
    text-transform: uppercase;
    font-weight: bold;
    padding: 6px 12px;
}
button#addVideo {
    float: none;
    margin: 10px 0;
}
li button:hover {
    background: #6A75A0;
    cursor: pointer;
}
li::after {
    clear: both;
}

a {
  color: #42b983;
}
input {
  border-radius: 8px 8px;
  border: 1px solid #ccc;
  padding: 10px;
  margin-bottom: 10px;
  
}
span {
    font-size: 12px;
}
input:focus{
  outline: none;
}
</style>
