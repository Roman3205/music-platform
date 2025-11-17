<template>
  <li class="flex items-center justify-between rounded-md hover:bg-gray-100 dark:hover:bg-gray-800" @mouseenter="isHover = true" @mouseleave="isHover = false">
    <div class="flex items-center w-full py-2">
        <div v-if="isHover" class="w-10 ml-3 mr-2 cursor-pointer">
            <Play v-if="true" :fillColor="[useColorMode().preference === 'light' ? '#181818' : '#FFFFFF']" :size="25" />
            <Pause v-else :fillColor="[useColorMode().preference === 'light' ? '#181818' : '#FFFFFF']" :size="25" />
        </div>
        <div v-else class="dark:text-white font-semibold w-10 ml-5">
            <span>{{ index }}</span>    
        </div>
        <div>
            <div
                :class="{'text-green-500': currentTrack && currentTrack.name === track.name}"
                class="dark:text-white font-semibold">
                    {{ track.name }}
            </div>
            <div class="text-sm font-semibold text-gray-400">{{ artist.name }}</div>
        </div>
    </div>
    <div class="flex items-center">
        <button type="button" v-if="isHover">
            <Heart fillColor="#1BD760" :size="22"/>
        </button>
    <div v-if="isTrackTime" class="text-xs mx-5 text-gray-400">
        {{ isTrackTime }}
    </div>
    </div>
  </li>
</template>

<script lang="ts" setup>
import Play from 'vue-material-design-icons/Play.vue'
import Pause from 'vue-material-design-icons/Pause.vue'
import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue';
import Heart from 'vue-material-design-icons/Heart.vue';

let isHover = ref(false)
let isTrackTime = ref(null)

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