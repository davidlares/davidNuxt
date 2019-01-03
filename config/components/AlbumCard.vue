<template lang="html">
  <div :key="album.id">
    <h4>{{album.title}}</h4>
    <a href="#">More info</a>
  </div>
</template>

<script>
export default {
  name: 'AlbumCard',
  props: {
    album: Object
  }
}
</script>

<style lang="css" scoped>
</style>
