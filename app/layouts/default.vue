<script setup lang="ts">
const route = useRoute()
import type { NavigationMenuItem } from '@nuxt/ui'
import { useSongStore } from '~/stores/song';
const useSong = useSongStore()
const { isPlaying, currentTrack } = storeToRefs(useSong)
onMounted(() => {
  isPlaying.value = false
})

const items = ref<NavigationMenuItem[][]>([
  [
        {
          label: 'Home',
          icon: 'i-lucide-house',
          to: '/'
        },
        {
          label: 'Search',
          icon: 'i-lucide-search',
          to: '/search'
        },
        {
          label: 'Library',
          icon: 'i-lucide-swatch-book',
          to: '/library'
        }
  ]
])
</script>

<template>
    <div>
         <UHeader>
            <template #title>
                <Logo class="h-6 w-auto" />
            </template>

            <template #right>
            <UColorModeButton />
            </template>

        </UHeader>
        <UMain>
            <UContainer class="flex">
                <UNavigationMenu orientation="vertical" :items="items" class="data-[orientation=vertical]:w-48 my-4" />
                <slot />
            </UContainer>
        </UMain>
        <MusicPlayer v-if="currentTrack" />
    </div>
</template>

