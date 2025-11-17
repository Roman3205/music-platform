<script setup lang="ts">
const route = useRoute()
import type { NavigationMenuItem } from '@nuxt/ui'

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
        },
        {
          label: 'Create Playlist',
          icon: 'i-lucide-plus',
          to: '/create-playlist'
        },
                {
          label: 'Liked Songs',
          icon: 'i-lucide-heart',
          to: '/liked-songs'
        },
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
            <UContainer class="flex ">
                <UNavigationMenu orientation="vertical" :items="items" class="data-[orientation=vertical]:w-48 my-4" />
                <slot />
            </UContainer>
        </UMain>
    </div>
</template>

