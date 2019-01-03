<template lang="html">
  <div class="">
    <h1>Album List</h1>
    <div v-for="album in albums" :key="album.id">
      <h4>{{album.title}}</h4>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import env from '../config/env'
export default {
  name: 'IndexPage', // component name
  data(){
    return {
      albums: []
    }
  },
  created(){
    // VueJS Hook
    axios.get(`${env.endpoint}/albums`)
    .then(res => {
      // client and also displayed on server side
      console.log(res)
      this.albums = res.data
    })
  }
}
</script>

<style lang="css" scoped>
</style>
