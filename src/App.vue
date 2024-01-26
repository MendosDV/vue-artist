<template>
  <div class="container">
    <div class="text-center p-2" v-html="title"></div>
    <div class="w-75 p-3 mx-auto">
      <ul class="list-group list-group-flush mb-4 rounded">
        <li class="list-group-item d-flex justify-content-between align-items-center" v-for="(artist, index) in artists" :key="index">
          <span>{{ artist.name }}</span>
          <svg type="button" @click="removeArtist(artist.name)" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16">
            <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5m2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5m3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0z"/>
            <path d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4zM2.5 3h11V2h-11z"/>
          </svg>
        </li>
      </ul>
      <p v-if="artists.length < 1">You have no artist in your list</p>
      <form @submit.prevent="addArtist" class="d-flex flex-row gap-3">
        <div class="d-flex flex-column flex-grow-1">
          <input class="form-control p-2 flex-grow-1" type="text" v-model.trim="newArtist" placeholder="Add new artist">
        </div>
        <button class="btn btn-primary p-2" type="submit">Add artist</button>
      </form>
    </div>
  </div>
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
