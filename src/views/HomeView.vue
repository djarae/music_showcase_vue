<template>
  <div class="flex flex-col lg:flex-row gap-6 h-[calc(100vh-140px)]">
    <!-- Song List (Sidebar on Desktop) -->
    <aside class="w-full lg:w-1/3 overflow-y-auto pr-2 custom-scrollbar">
      <div class="mb-4 flex items-center justify-between">
        <h2 class="text-xl font-bold border-b border-[var(--color-primary)] pb-1 w-full">AVAILABLE_TRACKS</h2>
      </div>

      <div class="flex flex-col gap-3">
        <div 
          v-for="song in songs" 
          :key="song.id"
          @click="selectSong(song)"
          class="
            p-3 border border-[var(--color-primary)]/30 rounded cursor-pointer
            hover:bg-[var(--color-primary)]/10 hover:border-[var(--color-primary)]
            transition-all duration-200 group
            flex items-center gap-3
          "
          :class="{ 'bg-[var(--color-primary)]/20 border-[var(--color-primary)]': currentSong?.id === song.id }"
        >
          <!-- Tiny Cover -->
          <div class="w-12 h-12 overflow-hidden border border-[var(--color-primary)]/50 relative">
             <img :src="song.cover" :alt="song.title" class="w-full h-full object-cover opacity-80 group-hover:opacity-100 grayscale group-hover:grayscale-0 transition-all"/>
          </div>
          
          <div class="flex-1 min-w-0">
            <h3 class="font-bold truncate text-sm group-hover:terminal-glow">{{ song.title }}</h3>
            <p class="text-xs opacity-70 truncate">{{ song.artist }}</p>
          </div>
          
          <div class="text-[10px] bg-[var(--color-primary)]/10 px-1 py-0.5 border border-[var(--color-primary)]/20">
            {{ song.genre.toUpperCase() }}
          </div>
        </div>
      </div>
    </aside>

    <!-- Player Area -->
    <main class="flex-1 flex flex-col">
      <TerminalCard class="h-full flex flex-col p-0 overflow-hidden relative">
        <div v-if="currentSong" class="flex-1 flex flex-col">
          <!-- Youtube Embed -->
          <div class="relative w-full h-0 pb-[56.25%] bg-black">
            <iframe 
              :src="`https://www.youtube.com/embed/${currentSong.youtubeId}?autoplay=1&rel=0`" 
              title="YouTube video player" 
              frameborder="0" 
              allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
              allowfullscreen
              class="absolute top-0 left-0 w-full h-full"
            ></iframe>
          </div>

          <!-- Song Info Block -->
          <div class="p-6 flex-1 flex flex-col justify-center items-start gap-4">
            <div>
              <h2 class="text-3xl md:text-5xl font-bold mb-2 terminal-glow">{{ currentSong.title }}</h2>
              <p class="text-xl md:text-2xl opacity-80">> {{ currentSong.artist }}</p>
            </div>
            
            <div class="flex gap-4 mt-auto w-full">
              <div class="text-sm border border-[var(--color-primary)] px-3 py-1">
                GENRE: {{ currentSong.genre }}
              </div>
              <div class="text-sm border border-[var(--color-primary)] px-3 py-1 flex-1 text-right">
                STATUS: PLAYING
              </div>
            </div>
          </div>
        </div>

        <div v-else class="flex-1 flex items-center justify-center flex-col text-center p-8 opacity-50">
          <div class="text-6xl mb-4">?</div>
          <p class="text-xl">NO_TRACK_SELECTED</p>
          <p class="text-sm">SELECT A TRACK FROM THE LIST TO INITIALIZE PROTOCOL</p>
        </div>
      </TerminalCard>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import songsData from '../data/songs.json'
import TerminalCard from '../components/shared/TerminalCard.vue'

const songs = ref(songsData)
const currentSong = ref(null)

const selectSong = (song) => {
  currentSong.value = song
}
</script>

<style scoped>
.custom-scrollbar::-webkit-scrollbar {
  width: 6px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  background: black;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: var(--color-primary);
  border-radius: 2px;
}
.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: var(--color-primary-dark);
}
</style>
