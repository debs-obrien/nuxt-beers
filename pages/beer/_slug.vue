<template>
  <div>
    <div
      class="md:flex shadow-lg mx-6 md:mx-auto my-40 max-w-lg md:max-w-2xl h-64"
    >
      <img
        class="h-full w-full md:w-1/3 object-cover rounded-lg rounded-r-none pb-5/6"
        :src="beer.image_url"
        alt="bag"
      />
      <div class="w-full md:w-2/3 px-4 py-4 bg-white rounded-lg">
        <div class="flex items-center">
          <h2 class="text-xl text-gray-800 font-medium mr-auto">
            {{ beer.name }}
          </h2>
          <p class="text-gray-800 font-semibold tracking-tighter">
            ${{ beer.price }}
          </p>
        </div>
        <p class="text-sm text-gray-700 mt-4">
          {{ beer.category }}
        </p>
        <p class="text-sm text-gray-700 mt-4">Brewer: {{ beer.brewer }}</p>
        <p class="text-sm text-gray-700 mt-4">ABV: {{ beer.abv }}</p>
        <p class="text-sm text-gray-700 mt-4">Size: {{ beer.size }}</p>
        <div class="flex items-center justify-end mt-4 top-auto">
          <button
            class="bg-blue-600 text-gray-200 px-2 py-2 rounded-md"
            @click="sendToCart"
          >
            Purchase
          </button>
        </div>
      </div>
    </div>
    <div></div>
    <div>
      <h2 class="text-center font-bold text-xl">Related Products</h2>
      <ProductCard />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, $axios, params }) {
    const beer = await $axios.$get(
      `https://api.nuxtjs.dev/beers/${params.slug}`
    )

    return { beer }
  },
  methods: {
    sendToCart() {
      this.$toast.show('Adding to Cart...').goAway(1000)
    },
  },
}
</script>
