<template lang="html">
  <div class="">
    <h1>Album List</h1>
    <AlbumCard :album="album" v-for="album in albums" />
  </div>
</template>

<script>
import axios from 'axios'
import env from '../config/env'
import AlbumCard from '../config/components/AlbumCard.vue'
export default {
  name: 'IndexPage', // component name
  components: {
    AlbumCard
  },
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
