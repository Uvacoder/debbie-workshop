<template>
  <div class="bg-gray-100 rounded-md border h-full">
    <div class="container mx-auto p-4">
      <nuxt-link to="/reviews" class="block pb-6">
        Back to the reviews
      </nuxt-link>
      <header>
        <h3 class="font-bold text-2xl pb-2">{{ review.title }}</h3>
      </header>
      <p class="pb-6">{{ review.description }}</p>
      <NuxtContent :document="review" class="prose" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const review = await $content(`reviews/${params.slug}`).fetch()
    return {
      review,
    }
  },
}
</script>
