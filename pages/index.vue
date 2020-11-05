<template>
  <div class="container flex flex-col">
    <TheHero />
    <div>
      <h2 class="font-bold text-xl m-8">Look at all those Beers</h2>
      <ProductCard />
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
