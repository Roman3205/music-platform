<template>
  <div v-if="randomColor" :style="{ backgroundColor: randomColor }" class="rounded-lg overflow-hidden aspect-square p-4 flex relative flex-col items-center justify-center gap-2">
    <NuxtImg :src="image" class="w-32 h-32 lg:h-28 lg:w-28 rounded-md object-cover rotate-20 bottom-3 absolute contrast-[0.55] -right-3.5" />
    <h3 class="text-white font-semibold text-lg text-center absolute top-3 left-3">{{ category }}</h3>
  </div>
</template>

<script lang="ts" setup>
import uniqolor from 'uniqolor';

const props = defineProps<{
    category: string;
    image: string;
}>()
let randomColor = useState('color-' + props.image, () => '')
randomColor.value = uniqolor.random().color

</script>

<style>

</style>