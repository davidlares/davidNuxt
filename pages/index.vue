<template lang="html">
  <div class="container">
    <header>
      <h1 class="title">Album List</h1>
    </header>
    <div class="columns is-multiline">
      <AlbumCard :album="album" v-for="album in albums" :key="album.id" />
    </div>
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
      this.albums = res.data
    })
  }
}
</script>
