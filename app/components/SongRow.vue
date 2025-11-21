<template>
  <li class="flex items-center justify-between rounded-md hover:bg-gray-100 dark:hover:bg-gray-800" @mouseenter="isHover = true" @mouseleave="isHover = false">
    <div class="flex items-center w-full py-2">
        <div v-if="isHover" class="w-10 ml-3 mr-2 cursor-pointer">
            <Play v-if="!isPlaying" @click="useSong.playOrPauseThisSong(artist, track)" :fillColor="colorMode.preference === 'light' ? '#181818' : '#FFFFFF'" :size="25" />
            <Play v-else-if="isPlaying && currentTrack.name!==track.name" @click="useSong.loadSong(artist, track)"  :fillColor="colorMode.preference === 'light' ? '#181818' : '#FFFFFF'" :size="25" />
            <Pause v-else @click="useSong.playOrPauseSong()"  :fillColor="colorMode.preference === 'light' ? '#181818' : '#FFFFFF'" :size="25" />
        </div>
        <div v-else class="dark:text-white font-semibold w-10 ml-5">
            <span :class="{'text-green-500': currentTrack && currentTrack.name === track.name}">{{ index }}</span>    
        </div>
        <div>
            <div
                class="dark:text-white font-semibold"
                :class="{'text-green-500!': currentTrack && currentTrack.name === track.name}"
                >
                    {{ track.name }}
            </div>
            <div class="text-sm font-semibold text-gray-400">{{ artist.name }}</div>
        </div>
    </div>
    <div class="flex items-center">
    <div v-if="isTrackTime" class="text-xs mx-5 text-gray-400">
        {{ isTrackTime }}
    </div>
    </div>
  </li>
</template>

<script lang="ts" setup>
import Play from 'vue-material-design-icons/Play.vue'
import Pause from 'vue-material-design-icons/Pause.vue'
import { useSongStore } from '~/stores/song';

const useSong = useSongStore()
const { isPlaying, currentTrack } = storeToRefs(useSong)

let isHover = ref(false)
let isTrackTime = ref(null)

const colorMode = useColorMode()

const props = defineProps<{
    track: object;
    artist: object;
    index: number;
}>()

const {track, artist, index} = toRefs(props)

onMounted(() => {
    const audio = new Audio(track.value.path)
    audio.addEventListener('loadedmetadata', () => {
        const duration = audio.duration
        const minutes = Math.floor(duration / 60)
        const seconds = Math.floor(duration % 60)
        isTrackTime.value = minutes + ':' + seconds.toString().padStart(2, '0')
    })
})
</script>

<style>

</style>