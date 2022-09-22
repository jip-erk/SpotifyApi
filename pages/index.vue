<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <button @click="getActiveSong" class="btn btn-primary">getActive song</button>
      </v-card>
    </v-col>
    <v-col cols="12" sm="8" md="6" v-if="responseData">
      <v-card class="cont py-4 d-flex justify-center">
        <a class="imga" :href="responseData.item.external_urls.spotify">
          <img :src="responseData.item.album.images[0].url" alt="cover">
        </a>

        <h1>{{responseData.item.name}}</h1>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
  import async from 'asynckit/lib/async';
import axios from 'axios'
export default {
  name: 'IndexPage',
  data: () => ({
    access_token: '',
    refresh_token: '',
    responseData: null,

  }),
  async mounted(){
    this.access_token = this.$route.query.access_token || null;
    this.refresh_token = this.$route.query.refresh_token || null;
    
    //retunr userdata from spotify api using access token and refresh token and axios
    await axios.get('https://api.spotify.com/v1/me', {
      headers: {
        'Authorization': 'Bearer ' + this.access_token
      }
    })
    .then(function (response) {
      console.log(response);
    })
    .catch(function (error) {
      console.log(error);
    });

 //spotify api get  users followers list 
    await axios.get('https://api.spotify.com/v1/me/followers', {
      headers: {
        'Authorization': 'Bearer ' + this.access_token
      }
    })
    .then(function (response) {
      console.log(response);
    })
    .catch(function (error) {
      console.log(error);
    });
    

    
    //log active song to console 
    this.getActiveSong();
  },

  //get folwoers list from spotify api using access token and refresh token and axios
 
  
   
    
  
  //get active song playing from spotify api using access token and refresh token and axios
  methods: {
    getActiveSong(){
      axios.get('https://api.spotify.com/v1/me/player/currently-playing', {
        headers: {
          'Authorization': 'Bearer ' + this.access_token
        }
      })
      .then((response) => {
       this.responseData = response.data;
       console.log(this.responseData);
      })
      .catch(function (error) {
        console.log(error);
      });
    }
  }


  
}
</script>

<style>
.cont{
  height: 100%;
  width: 100%;
  max-height: 150px;
  background-color: #000;
  position: relative;
}
.imga{
  position: relative;

}

img{
  position: relative;
  height: 100%;
}

h1{
  position: absolute;
}
</style>
