<template>
  <div>hi</div>
</template>

<script>
  import axios from 'axios'
export default {
  data(){
    return {
      client_id: '901002c364b24a2089f421f8dfc1a12e',
      client_secret: '4d74d27455144deca2c76006036b8469',
      code: '',
      state: '',
    }
  },
  mounted(){
    this.code = this.$route.query.code || null;
    this.state = this.$route.query.state || null;

    //return refresh token from spotify api using code
 
  },
  methods:{

  },

}
</script>

<style>

</style>