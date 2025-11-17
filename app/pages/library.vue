<template>
  <div class="w-full h-screen p-4 px-6 flex flex-col gap-6">
    <h2 class="text-2xl">{{ artist.name }}</h2>
    <div class="flex items-center w-full relative">
        <NuxtImg width="140" :src="artist.albumCover" class="rounded-md" />
        <div class="w-full ml-5">
            <div class="text-3xl absolute w-full hover:underline cursor-poiner top-0 font-semibold">
                {{ artist.name }}
            </div>
            <div class="text-gray-500 text-[13px] flex">
                <h3>Album</h3>
                <div class="ml-2 flex">
                    <div class="circle mt-2 mr-2"></div>
                    <span class="-ml-0.5">{{ artist.releaseYear }}</span>
                </div>
                <div class="ml-2 flex">
                    <div class="circle mt-2 mr-2"></div>
                    <span class="-ml-0.5">{{ artist.tracks.length }}</span>
                </div>
            </div>
            <div class="absolute flex gap-4 items-center justify-start bottom-0 mb-1.5">
                <button class="rounded-full p-1 bg-black dark:bg-white" type="button">
                    <Play v-if="true" :fillColor="[useColorMode().preference === 'dark' ? '#181818' : '#FFFFFF']" :size="25" />
                    <Play v-else fillColor="#181818" :size="25" />
                </button>
                <button class=" rounded-full p-1" type="button">
                    <Heart v-if="true" fillColor="#1BD760" :size="30" />
                </button>
                <button class="rounded-full p-1" type="button">
                    <DotsHorizontal :fillColor="[useColorMode().preference === 'light' ? '#181818' : '#FFFFFF']" :size="25" />
                </button>
            </div>
            
        </div>
        
    </div>
    <div class="flex items-center justify-between my-4 px-5 pt-2">
        <div class="flex items-center justify-between text-gray-400">
            <div class="mr-7">#</div>
            <div class="text-sm">Title</div>
        </div>
        <div><ClockTimeThreeOutline :fillColor="[useColorMode().preference === 'light' ? '#181818' : '#FFFFFF']" :size="18"/></div>
    </div>
    <ul class="w-full" v-for="track, index in artist.tracks" :key="track">
        <SongRow :artist="artist" :track="track" :index="++index"/>
    </ul>
  </div>
</template>

<script lang="ts" setup>
import artist from '~~/artist.json'
import Play from 'vue-material-design-icons/Play.vue'
import Pause from 'vue-material-design-icons/Pause.vue'
import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue';
import Heart from 'vue-material-design-icons/Heart.vue';
import ClockTimeThreeOutline from 'vue-material-design-icons/ClockTimeThreeOutline.vue';
</script>

<style scoped>
.circle {
    width: 4px;
    height: 4px;
    background-color: gray;
    border-radius: 50%;
}
</style>