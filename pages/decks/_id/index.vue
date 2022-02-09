<template>
  <h1>Your decks {{ $route.params.id }} is active</h1>
</template>

<script>
export default {
  name: "IndexID",
  validate(ctx) {

    return /^[0-9]{9,12}$/.test(ctx.params.id)
  }
}
</script>
