<template>
  <div
    class="w-screen flex flex-row items-center p-1 justify-between bg-white shadow-xs sticky top-0"
  >
    <NuxtLink to="/" class="ml-8 text-lg text-gray-700 hidden md:flex"
      >Nuxt Beers</NuxtLink
    >

    <div class="flex flex-row-reverse mr-4 ml-4 md:hidden">
      <i class="fas fa-bars"></i>
    </div>
    <div class="flex flex-row-reverse mr-8 hidden md:flex">
      <NuxtLink
        to="/beers"
        class="text-gray-700 text-center bg-gray-400 px-4 py-2 m-2"
      >
        Beers
      </NuxtLink>
      <NuxtLink
        to="/reviews"
        class="text-gray-700 text-center bg-gray-400 px-4 py-2 m-2"
      >
        Reviews
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {}
</script>
