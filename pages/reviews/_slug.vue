<template>
  <div>
    <div class="flex flex-wrap md items-center h-screen">
      <div class="bg-white w-full md:w-1/2 h-screen">
        <div class="mx-32">
          <NuxtLink to="/reviews" class="mt-4 block">Back to reviews</NuxtLink>
          <h1 class="text-6xl font-bold mt-8">{{ review.title }}</h1>

          <div class="flex mt-16 font-light text-gray-500">
            <div class="pr-4">
              <span class="uppercase">Country</span>
              <p class="text-2xl text-gray-900 font-semibold pt-2">
                {{ review.country }}
              </p>
            </div>
            <div class="pr-4">
              <span class="uppercase">Type</span>
              <p class="text-2xl text-gray-900 font-semibold pt-2">
                {{ review.type }}
              </p>
            </div>
          </div>

          <div class="description w-full mt-16 text-gray-500 text-sm">
            <NuxtContent
              class="prose prose-sm sm:prose prose-md mx-auto"
              :document="review"
            />
            <prev-next :prev="prev" :next="next" class="my-8" />
          </div>
        </div>
      </div>
      <div class="bg-red-600 w-full md:w-1/2 h-screen">
        <img :src="review.img" class="h-screen w-full" :alt="review.title" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const review = await $content('reviews', params.slug).fetch()
    const [prev, next] = await $content('reviews')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()
    return { review, prev, next }
  },
}
</script>
