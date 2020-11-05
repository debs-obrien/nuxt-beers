<template>
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
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      default: () => {},
    },
  },
}
</script>
