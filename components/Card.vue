<template>
  <div class="bg-gray-100 rounded-md p-4 border h-full">
    <header>
      <h3 class="font-bold text-2xl pb-2">{{ river.title }}</h3>
    </header>
    <img :src="river.image" class="object-cover h-32 w-full pb-2" />
    <p class="h-24 overflow-y-hidden">{{ river.description }}</p>
  </div>
</template>

<script>
export default {
  props: {
    river: {
      type: Object,
      default: () => {
        return {}
      },
    },
  },
}
</script>
