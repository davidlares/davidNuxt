<template lang="html">
  <h1>Hello, World</h1>
</template>

<script>
import axios from 'axios'
import env from '../config/env'
export default {
  name: 'IndexPage', // component name
  data(){
    return {
      albums: {}
    }
  },
  created(){
    // VueJS Hook
    axios.get(`${env.endpoint}/albums`)
    .then(res => {
      // client and also displayed on server side
      console.log(res)
    })
  }
}
</script>

<style lang="css" scoped>
</style>
