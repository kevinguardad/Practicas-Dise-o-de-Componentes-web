<script setup>
import MovieCard from './MovieCard.vue'

defineProps({
  category: {
    type: Object,  // { name, icon, color }
    required: true
  },
  peliculas: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['seleccionar'])
</script>

<template>
  <div class="category-container">
    <h3 class="category-title">
      {{ category.icon }} {{ category.name }}
    </h3>
    <div class="scroll-container">
      <div
        v-for="item in peliculas"
        :key="item.id"
        class="movie-wrapper"
      >
        <MovieCard
          :movie="item"
          @seleccionar="emit('seleccionar', $event)"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
.category-container {
  margin-bottom: 40px;
  width: 100%;
}
.category-title {
  font-size: 1.25rem;
  margin-bottom: 16px;
}
.scroll-container {
  display: flex;
  gap: 20px;
  overflow-x: auto;
  padding-bottom: 16px;
  scroll-snap-type: x mandatory;
  scrollbar-width: none;
}
.scroll-container::-webkit-scrollbar {
  display: none;
}
.movie-wrapper {
  flex: 0 0 auto;
  width: 220px;
  scroll-snap-align: start;
}
</style>