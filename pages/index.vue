<template>
  <div class="container mx-auto px-4">
    <header class="py-4">
      <h1 class="text-3xl font-bold">debbie-workshop</h1>
    </header>
    <div class="flex flex-wrap items-center justify-center">
      <LazyBaseAlert v-if="show" />
      <BaseButton @click="toggleAlert" />
      <nuxt-link class="font-bold px-3" to="/about">About</nuxt-link>
      <nuxt-link class="font-bold px-3" to="/asyncdata">
        AsyncData example
      </nuxt-link>
      <nuxt-link class="font-bold px-3" to="/rivers">Rivers</nuxt-link>
      <nuxt-link class="font-bold px-3" to="/reviews">Reviews</nuxt-link>
    </div>
    <p v-if="$fetchState.pending">Is fetching...</p>
    <p v-else-if="$fetchState.error">Ooops!</p>
    <div v-else class="pt-4 flex flex-wrap md:-mr-4">
      <BaseButton class="w-full md:pr-4" @click="$fetch" />
      <div
        v-for="river in rivers"
        :key="river.slug"
        class="w-full md:w-1/2 lg:w-1/3 py-4 md:pr-4"
      >
        <Card :river="river" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async fetch() {
    this.rivers = await fetch('https://api.nuxtjs.dev/rivers').then((res) =>
      res.json()
    )
  },
  data() {
    return {
      show: false,
      rivers: [],
    }
  },
  methods: {
    toggleAlert() {
      this.show = !this.show
    },
  },
}
</script>
