<template lang="html">
  <div>
    <a href="#">Back</a>
    <h2>{{album.title}}</h2>
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
  created(){
    let id = this.$route.params.id
    axios.get(`${env.endpoint}/albums/${id}`)
    .then(album => {
      this.album = album.data
    })
    axios.get(`${env.endpoint}/albums/${id}/photos`)
    .then(photos => {
      this.photos = photos.data
    })
  }
}
</script>

<style lang="css" scoped>
  .container {
    text-align: center;
  }
  .title {
    margin-top: 100px;
  }
</style>
