<template>
  <div v-html="title"></div>
  <ul>
    <li v-for="(artist, index) in artists" :key="index">
      {{ artist.name }}
      <button @click="removeArtist(artist.name)">x</button>
    </li>
  </ul>
  <p v-if="artists.length < 1">You have no artist in your list</p>
  <form @submit.prevent="addArtist">
    <input type="text" v-model.trim="newArtist" placeholder="Add new artist">
    <button class="btn btn-primary" type="submit">Add artist</button>
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
    },
    removeArtist(artist) {
      this.artists = this.artists.filter((a) => a.name != artist)
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
