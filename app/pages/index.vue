<template>
  <div class="w-full h-screen p-4 px-6 flex flex-col gap-6">
    <div class="flex flex-col">
      <h2 class="text-2xl">Podcasts to make you smarter</h2>
    <div class="grid grid-cols-2 gap-5 mt-4 md:grid-cols-3 lg:grid-cols-4">
      <UPageCard
    v-for="card in cards"
    :key="card.title"
    size
    :title="card.title"
    :description="card.description"
    orientation="vertical"
    reverse
  >
    <NuxtImg :src="card.img" class="w-full rounded-lg" />
  </UPageCard>
    </div>
    </div>
    <div class="flex flex-col">
      <h2 class="text-2xl">Recommended songs</h2>
    <div class="grid grid-cols-2 gap-5 mt-4 md:grid-cols-3 lg:grid-cols-4">
      <UPageCard
    v-for="card in cards"
    :key="card.title"
    size
    :title="card.title"
    :description="card.description"
    orientation="vertical"
    reverse
  >
    <NuxtImg :src="card.img" class="w-full rounded-lg" />
  </UPageCard>
    </div>
    </div>
    <div class="flex flex-col">
      <h2 class="text-2xl">Recommended radio</h2>
    <div class="grid grid-cols-2 gap-5 my-4 md:grid-cols-3 lg:grid-cols-4">
      <UPageCard
    v-for="card in cards"
    :key="card.title"
    size
    :title="card.title"
    :description="card.description"
    orientation="vertical"
    reverse
  >
    <NuxtImg :src="card.img" class="w-full rounded-lg" />
  </UPageCard>
    </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const cards = ref([
  {
        title: 'Title',
    description:
      'Subtitle',
      img: 'https://picsum.photos/id/30/300/300'
  },
  {
        title: 'Title',
    description:
      'Subtitle',
    img: 'https://picsum.photos/id/45/300/300'
  },
  {
    title: 'Title',
    description:
      'Subtitle',
    img: 'https://picsum.photos/id/65/300/300'
  },
  {
    title: 'Title',
    description:
      'Subtitle',
    img: 'https://picsum.photos/id/67/300/300'
  }
])
</script>

<style>

</style>