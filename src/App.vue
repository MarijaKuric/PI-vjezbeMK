<script setup>
import { ref, computed } from 'vue';

const filmovi = [
  { 
    naslov: "Gospodar prstenova: Prstenova družina", 
    slika: "https://m.media-amazon.com/images/I/71lKy8RoFUL._AC_UF1000,1000_QL80_.jpg"
  },
  { 
    naslov: "Gospodar prstenova: Dvije kule", 
    slika: "https://m.media-amazon.com/images/M/MV5BMGQxMDdiOWUtYjc1Ni00YzM1LWE2NjMtZTg3Y2JkMjEzMTJjXkEyXkFqcGc@._V1_FMjpg_UX1000_.jpg"
  },
  { 
    naslov: "Gospodar prstenova: Povratak kralja", 
    slika: "https://m.media-amazon.com/images/M/MV5BMTZkMjBjNWMtZGI5OC00MGU0LTk4ZTItODg2NWM3NTVmNWQ4XkEyXkFqcGc@._V1_.jpg"
  }
];

const isDarkMode = ref(true);

const promjeniPozadinu = () => {
  isDarkMode.value = !isDarkMode.value;
};

const okvirKlasa = computed(() => isDarkMode.value 
  ? 'bg-gradient-to-r from-emerald-950 to-indigo-950 text-white' 
  : 'bg-gradient-to-r from-emerald-300 to-indigo-300 text-gray-900'
);
</script>

<template>
  <div class="min-h-screen flex items-center justify-center p-4 transition-colors duration-300" :class="isDarkMode ? 'bg-gray-900' : 'bg-white'">
    
    <div class="p-8 rounded-2xl w-full md:w-[1024px] border-2 border-white/20 transition-all duration-300 relative shadow-2xl" :class="okvirKlasa">
      
      <button @click="promjeniPozadinu" 
        class="fixed top-4 right-4 bg-gray-800 text-white p-2 rounded-full focus:outline-none shadow-lg hover:bg-gray-700 transition-all">
        Prebaci na {{ isDarkMode ? 'svijetli' : 'tamni' }} način
      </button>

      <h1 class="text-5xl font-bold text-center" :class="isDarkMode ? 'text-teal-100' : 'text-teal-800'">
        Pozdrav, ja sam 
        <span :class="isDarkMode ? 'text-cyan-400' : 'text-cyan-600'"> Marija Kurić</span>
      </h1>

      <h2 class="text-xl text-center mb-6" :class="isDarkMode ? 'text-teal-100/75' : 'text-teal-800/75'">
        Moji omiljeni filmovi:
      </h2>

      <div class="flex justify-center gap-6">
        <div v-for="film in filmovi" :key="film.naslov" class="w-[320px] h-[480px] flex-shrink-0 overflow-hidden rounded-lg shadow-lg transition-transform duration-300 hover:scale-105 hover:shadow-xl">
          <img :src="film.slika" :alt="film.naslov" class="w-full h-full object-cover">
        </div>
      </div>

      <div class="flex justify-center gap-6 mt-4 text-xl" :class="isDarkMode ? 'text-teal-100' : 'text-teal-800'">
        <span v-for="film in filmovi" :key="film.naslov">{{ film.naslov }}</span>
      </div>

    </div>
  </div>
</template>
