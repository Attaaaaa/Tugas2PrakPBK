<template>
  <div id="app">
    <!-- Judul -->
    <h1>Nonton Konser Virtual</h1>

    <!-- Pemilihan genre musik -->
    <div>
      <h2>Pilih Genre Musik:</h2>
      <button @click="selectGenre('Rock')">Rock</button>
      <button @click="selectGenre('Pop')">Pop</button>
      <button @click="selectGenre('Classic')">Classic</button>
    </div>

    <!-- Informasi Konser -->
    <div v-if="selectedGenre">
      <h2>Konser {{ selectedGenre }}</h2>
      <p>Selamat datang di konser {{ selectedGenre }}!</p>
      <p>Tetaplah bersemangat dan hibur dirimu!</p>
    </div>

    <!-- Tombol untuk memulai konser -->
    <button v-if="selectedGenre" @click="startConcert">Mulai Konser</button>

    <!-- Animasi lampu panggung saat konser berlangsung -->
    <div v-if="isConcertStarted" :class="'stage-lights ' + selectedGenre.toLowerCase()"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedGenre: '', // Genre musik yang dipilih
      isConcertStarted: false // Status apakah konser sudah dimulai atau belum
    };
  },
  methods: {
    // Memilih genre musik untuk konser
    selectGenre(genre) {
      this.selectedGenre = genre;
    },
    // Memulai konser
    startConcert() {
      this.isConcertStarted = true;
    }
  }
};
</script>

<style scoped>
/* Animasi lampu panggung */
.stage-lights {
  width: 100%;
  height: 200px;
  animation: stageLights 2s infinite alternate-reverse;
}

/* Add specific background colors for each genre */
.rock {
  background: linear-gradient(to right, #ff0000, #660000);
}

.pop {
  background: linear-gradient(to right, #ffcc00, #333300);
}

.classic {
  background: linear-gradient(to right, #9966ff, #330066);
}

@keyframes stageLights {
  0% { opacity: 0.5; }
  100% { opacity: 1; }
}
</style>
