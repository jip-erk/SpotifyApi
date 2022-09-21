<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
     
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
  import axios from 'axios'
export default {
  name: 'IndexPage',
  data: () => ({
    access_token: '',
    refresh_token: '',

  }),
  mounted(){
    this.access_token = this.$route.query.access_token || null;
    this.refresh_token = this.$route.query.refresh_token || null;
    
    //retunr userdata from spotify api using access token and refresh token and axios
    axios.get('https://api.spotify.com/v1/me', {
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
  },
  
}
</script>
