<template>
  <div class="flex flex-wrap">
    <p v-if="$fetchState.pending">Fetching beers...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>

    <div
      v-for="product in beers"
      v-else
      :key="product.id"
      classs="flex flex-col"
    >
      <div class="max-w-sm rounded overflow-hidden shadow-lg m-4">
        <NuxtLink :to="`/beer/${product.slug}`">
          <img class="w-full" :src="product.image_url" :alt="product.name" />
        </NuxtLink>
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">
            <NuxtLink :to="`/beer/${product.slug}`">
              {{ product.name }}
            </NuxtLink>
          </div>
          <p class="text-gray-700 text-base">
            {{ product.category }}
          </p>
        </div>
        <div class="px-6 pt-4 pb-2">
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >{{ product.type }}</span
          >
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >{{ product.brewer }}</span
          >
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >{{ product.abv }}</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async fetch() {
    this.beers = await this.$axios.$get('https://api.nuxtjs.dev/beers')
  },
  data() {
    return {
      beers: {},
    }
  },
}
</script>
