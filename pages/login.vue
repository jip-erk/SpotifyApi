<template>
  <v-row>
    <v-col class="text-center">
      <NuxtLink to="/login">
        <button >login</button>
      </NuxtLink>
    </v-col>
  </v-row>
</template>

<script>
export default {

  name: 'InspirePage',
  actions: {

  },
  data(){
    return {
      client_id: '901002c364b24a2089f421f8dfc1a12e',
      client_secret: '4d74d27455144deca2c76006036b8469',
      redirect_uri: 'http://localhost:3000/callback',
    }
  },
  methods: {
    login(){
      // const counter = useCookie('counter')
      // counter.value = counter.value || Math.round(Math.random() * 1000)
      
      var scope = 'user-read-private user-read-email';
      //nuxt redirect to spotify login 

      // window.location = 'https://accounts.spotify.com/authorize' +
      //   '?response_type=code' +
      //   '&client_id=' + this.client_id +
      //   (scope ? '&scope=' + encodeURIComponent(scope) : '') +
      //   '&redirect_uri=' + this.redirect_uri;
    },
  
  }
}
</script>
