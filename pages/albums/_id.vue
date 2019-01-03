<template lang="html">
  <div class="container">
    <header>
      <nuxt-link to="/">Back</nuxt-link>
      <h2>{{album.title}}</h2>
    </header>
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
        <img :src="photo.url" :alt="photo.title">
      </div>
    </div>
  </div>
</template>

<script>
import router from 'vue-router'
import axios from 'axios'
import env from '../../config/env'
export default {
  name: 'AlbumPage',
  data(){
    return {
      album: {},
      photos: []
    }
  },
  created: async function(){
    // refactoring async methods
    let albumResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}`);
    this.album = albumResponse.data
    let photoResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`)
    this.photos = photoResponse.data
  }
}
</script>

<style lang="css" scoped>
  .container {
    text-align: center;
  }
  header {
    margin-top: 100px;
    margin-bottom: 100px;
  }
</style>
