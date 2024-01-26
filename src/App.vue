<template>
  <div v-html="title"></div>
  <ul>
    <li v-for="(artist, index) in artists" :key="index"> {{ artist.name }}</li>
  </ul>
  <form @submit.prevent="addArtist">
    <input type="text" v-model.trim="newArtist" placeholder="Add new artist">
    <button type="submit">Add artist</button>
  </form>
</template>

<script>
export default {
  methods: {
    addArtist() {
      if(this.newArtist != '') {
        this.artists.push({ name: this.newArtist })
        this.newArtist = ''
      }
    }
  },
  data() {
    return {
      title: "<h1>List of artist</h1>",
      artists: [
        { name: '2pac' },
        { name: 'Drake' },
        { name: 'Bob Marley' },
        { name: 'PNL' },
        { name: 'Céline Dion' }
      ],
      newArtist: ''
    }
  }
}
</script>

<style>
* {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>
