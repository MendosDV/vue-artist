<template>
  <AppHeader />
  <div class="container">
    <ArtistsList />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import ArtistsList from './components/ArtistsList.vue'

export default {
  components: { AppHeader, ArtistsList }
}
</script>

<style>
</style>
