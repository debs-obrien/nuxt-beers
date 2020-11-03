<template>
  <div>
    <div class="filters flex flex-row justify-center mt-4">
      <button
        v-for="beerType in types"
        :key="beerType"
        class="uppercase mx-2 shadow bg-indigo-800 hover:bg-indigo-700 focus:shadow-outline focus:outline-none text-white text-xs py-3 px-10 rounded"
        @click="FilterBeersByType(beerType)"
      >
        {{ beerType }}
      </button>
      <button
        class="uppercase mx-2 shadow bg-indigo-600 hover:bg-indigo-700 focus:shadow-outline focus:outline-none text-white text-xs py-3 px-10 rounded"
        @click="FilterBeersByType('')"
      >
        clear filter
      </button>
    </div>
    <div class="flex flex-wrap">
      <ProductCardProps
        v-for="product in filteredBeers"
        :key="product.id"
        classs="flex flex-col"
        :product="product"
      />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const beers = await $axios.$get('https://api.nuxtjs.dev/beers')
    return { beers }
  },
  data() {
    return {
      type: '',
      types: ['Ale', 'Flavoured Malt', 'Malt', 'Lager'],
    }
  },
  computed: {
    filteredBeers() {
      return this.beers.filter((el) => el.type.match(this.type))
    },
  },
  methods: {
    FilterBeersByType(type) {
      this.type = type
    },
  },
}
</script>
