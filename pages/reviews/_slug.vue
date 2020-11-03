<template>
  <div class="flex flex-wrap md items-center">
    <div class="bg-white w-full md:w-1/2">
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
    <div class="w-full md:w-1/2">
      <img :src="review.img" class="w-full" :alt="review.title" />
    </div>
  </div>
</template>

<script>
export default {
  transition: 'slide-bottom',
  async asyncData({ $content, params }) {
    const review = await $content('reviews', params.slug).fetch()
    const [prev, next] = await $content('reviews')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()
    return { review, prev, next }
  },
  // head: {
  //   title: this.review.title,
  //   meta: [
  //     {
  //       hid: 'description',
  //       name: 'description',
  //       content: this.review.description,
  //     },
  //     { property: 'og:site_name', content: this.review.title },
  //     { hid: 'og:type', property: 'og:type', content: 'website' },
  //     {
  //       hid: 'og:url',
  //       property: 'og:url',
  //       content: 'http://nuxt-beers.surge.sh',
  //     },
  //     {
  //       hid: 'og:title',
  //       property: 'og:title',
  //       content: this.review.title,
  //     },
  //     {
  //       hid: 'og:description',
  //       property: 'og:description',
  //       content: this.review.description,
  //     },
  //     {
  //       hid: 'og:image',
  //       property: 'og:image',
  //       content: this.review.img,
  //     },
  //     { property: 'og:image:width', content: '740' },
  //     { property: 'og:image:height', content: '300' },
  //     { name: 'twitter:site', content: '@debs_obrien' },
  //     { name: 'twitter:card', content: 'summary_large_image' },
  //     {
  //       hid: 'twitter:url',
  //       name: 'twitter:url',
  //       content: 'http://nuxt-beers.surge.sh',
  //     },
  //     {
  //       hid: 'twitter:title',
  //       name: 'twitter:title',
  //       content: this.review.title,
  //     },
  //     {
  //       hid: 'twitter:description',
  //       name: 'twitter:description',
  //       content: this.review.description,
  //     },
  //     {
  //       hid: 'twitter:image',
  //       name: 'twitter:image',
  //       content: this.review.img,
  //     },
  //   ],
  // },
}
</script>
