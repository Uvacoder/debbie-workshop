<template>
  <div class="bg-gray-100 rounded-md border h-full">
    <img :src="river.image" class="w-full h-64 object-cover" />
    <div class="container mx-auto p-4">
      <nuxt-link to="/rivers">Back to the list</nuxt-link>
      <header>
        <h3 class="font-bold text-2xl pb-2">{{ river.title }}</h3>
      </header>
      <p>{{ river.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const river = await $axios.$get(
      `https://api.nuxtjs.dev/rivers/${params.slug}`
    )
    return {
      river,
    }
  },
}
</script>
