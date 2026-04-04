<script setup>
import MovieCard from './MovieCard.vue'

defineProps({
  peliculas: { type: Array, required: true }
})

const emit = defineEmits(['seleccionar'])
</script>

<template>
  <div class="section-container">
    <div class="section-header">
      <div class="icon-box gradient-pink">
        <!-- Ícono tendencia igual al diseño -->
        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <polyline points="23 6 13.5 15.5 8.5 10.5 1 18"/>
          <polyline points="17 6 23 6 23 12"/>
        </svg>
      </div>
      <div>
        <h2>Top 10 This Week</h2>
        <p>Most popular movies right now</p>
      </div>
    </div>
    <div class="movies-grid">
      <MovieCard
        v-for="item in peliculas"
        :key="item.id"
        :movie="item"
        @seleccionar="emit('seleccionar', $event)"
      />
    </div>
  </div>
</template>

<style scoped>
.section-container { margin-bottom: 40px; }
.section-header { display: flex; align-items: center; gap: 16px; margin-bottom: 32px; }
.icon-box { padding: 12px; border-radius: 12px; display: flex; align-items: center; justify-content: center; }
.gradient-pink { background: linear-gradient(135deg, #ec4899, #9333ea); }
.section-header h2 { font-size: 1.5rem; margin: 0; }
.section-header p { color: #9ca3af; font-size: 0.875rem; margin-top: 4px; }
.movies-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 24px;
}
</style>