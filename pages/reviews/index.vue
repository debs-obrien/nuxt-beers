<template>
  <div class="text-center font-bold text-xl">
    <h1>reviews</h1>
    <AppSearchInput />
    <ul class="divide-y divide-gray-200 flex flex-col">
      <li
        v-for="review in reviews"
        :key="review.id"
        class="py-4 flex space-x-3"
      >
        <img
          :src="review.img"
          :alt="review.title"
          class="h-20 w-20 rounded-full"
        />
        <div class="flex flex-col">
          <span class="text-sm leading-5 font-medium text-gray-900">
            <NuxtLink :to="`/reviews/${review.slug}`">
              {{ review.title }}
            </NuxtLink>
          </span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const reviews = await $content('reviews')
      .only(['title', 'slug', 'id', 'img'])
      .fetch()
    return { reviews }
  },
}
</script>
