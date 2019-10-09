<template>
  <div id="app" class="container">
    <h1 class="title is-1">Kaamelott</h1>
    <div v-for="quote in quotes" :key="quote" class="text">
      <p class="perceval">Perceval</p>

      <div class="quote">{{quote.citation}}</div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "app",
  data() {
    return {
      quotes: null
    };
  },
  mounted() {
    axios
      .get(
        `${"https://cors-anywhere.herokuapp.com/"}https://kaamelott.chaudie.re/api/all/livre/1/personnage/Perceval`
      )
      .then(response => (this.quotes = response.data.citation));
  }
};
</script>

<style lang="scss">
</style>
