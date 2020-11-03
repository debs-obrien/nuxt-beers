<template>
  <div class="text-center font-bold text-xl">
    <h1>reviews</h1>
    <AppSearchInput />

    <div class="grid md:grid-cols-2 sm:grid-cols-1 lg:grid-cols-3 m-5 mb-10">
      <div
        v-for="review in reviews"
        :key="review.id"
        class="bg-white overflow-hidden hover:bg-green-100 m-1 border border-gray-200 p-3"
      >
        <NuxtLink :to="`/reviews/${review.slug}`">
          <img
            :src="review.img"
            :alt="review.title"
            class="h-20 w-20 rounded-full"
          />
          <div class="m-2 text-justify text-sm">
            <p class="text-right text-xs">{{ review.updatedAt }}</p>
            <h2 class="font-bold text-lg h-2 mb-8">{{ review.title }}</h2>
            <p class="text-xs">
              {{ review.description }}
            </p>
          </div>
          <div class="w-full text-right mt-4">
            <span class="text-green-400 uppercase font-bold text-sm"
              >Read More</span
            >
          </div>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const reviews = await $content('reviews')
      .only(['title', 'slug', 'id', 'img', 'description'])
      .fetch()
    return { reviews }
  },
}
</script>
