<template>
  <div class="container mx-auto px-4">
    <header class="py-4">
      <h1 class="text-3xl font-bold">Rivers</h1>
      <nuxt-link to="/">Home</nuxt-link>
    </header>
    <div class="pt-4 flex flex-wrap md:-mr-4">
      <nuxt-link
        v-for="river in rivers"
        :key="river.slug"
        :to="`/rivers/${river.slug}`"
        class="block w-full md:w-1/2 lg:w-1/3 py-4 md:pr-4"
      >
        <Card :river="river" />
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const rivers = await $axios.$get('https://api.nuxtjs.dev/rivers')
    return {
      rivers,
    }
  },
}
</script>
