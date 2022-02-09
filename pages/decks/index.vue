<template>
  <div>
    <h1>Your Decks , please enter number of decks to show:</h1>
    <input v-model="deckID" type="text" placeholder="Please enter deckID">
    <button @click="showDeck">Go to Decks</button>
  </div>
</template>


<script >
export default {
  name: "DeckID",
  data(){
    return {
      deckID: '1'
    }
  },
  methods: {
    showDeck(){
      this.$router.push(`/decks/${this.deckID}`)
    }
  }
}
</script>
