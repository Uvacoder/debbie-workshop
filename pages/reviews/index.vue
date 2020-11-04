<template>
  <div class="container mx-auto px-4">
    <header class="py-4">
      <h1 class="text-3xl font-bold">Beer reviews</h1>
      <nuxt-link to="/">Home</nuxt-link>
    </header>
    <div class="pt-4 flex flex-wrap md:-mr-4">
      <nuxt-link
        v-for="review in reviews"
        :key="review.slug"
        :to="`/reviews/${review.slug}`"
        class="block w-full md:w-1/2 lg:w-1/3 py-4 md:pr-4"
      >
        <div class="bg-gray-100 rounded-md p-4 border h-full">
          <header>
            <h3 class="font-bold text-2xl pb-2">{{ review.title }}</h3>
          </header>
          <p class="h-24 overflow-y-hidden">{{ review.description }}</p>
        </div>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const reviews = await $content('reviews').fetch()
    return {
      reviews,
    }
  },
}
</script>
