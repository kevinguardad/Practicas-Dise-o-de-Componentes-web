<script setup>
import TopMovies from '../components/TopMovies.vue'
import MovieCategory from '../components/MovieCategory.vue'
import { ref, computed } from 'vue'

const activeTab = ref('Recommendations')
const tabs = ['Recommendations', 'Search', 'Watchlist (0)', 'History (0)', 'Reviews (0)']
const isDark = ref(true)

const categories = [
  { id: 1, name: 'Action',    icon: '💥', color: '#ef4444' },
  { id: 2, name: 'Drama',     icon: '🎭', color: '#8b5cf6' },
  { id: 3, name: 'Comedy',    icon: '😂', color: '#f59e0b' },
  { id: 4, name: 'Sci-Fi',    icon: '🚀', color: '#06b6d4' },
  { id: 5, name: 'Horror',    icon: '👻', color: '#6b7280' },
  { id: 6, name: 'Romance',   icon: '❤️', color: '#ec4899' },
  { id: 7, name: 'Thriller',  icon: '🔪', color: '#d97706' },
  { id: 8, name: 'Animation', icon: '🎨', color: '#10b981' },
]

const peliculas = ref([
  { id: 1,  rank: 1,  title: 'The Shawshank Redemption', year: 1994, rating: 9.3, genre: 'Drama',
    image: 'https://m.media-amazon.com/images/M/MV5BNDE3ODcxYzMtY2YzZC00NmNlLWJiNDMtZDViZWM2MzIxZDYwXkEyXkFqcGdeQXVyNjAwNDUxODI@._V1_.jpg' },
  { id: 2,  rank: 2,  title: 'The Dark Knight',          year: 2008, rating: 9.0, genre: 'Action, Crime',
    image: 'https://m.media-amazon.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_.jpg' },
  { id: 3,  rank: 3,  title: 'Pulp Fiction',             year: 1994, rating: 8.9, genre: 'Crime, Drama',
    image: 'https://m.media-amazon.com/images/M/MV5BNGNhMDIzZTUtNTBlZi00MTRlLWFjM2ItYzViMjE3YzI5MjljXkEyXkFqcGdeQXVyNzkwMjQ5NzM@._V1_.jpg' },
  { id: 4,  rank: 4,  title: 'Inception',                year: 2010, rating: 8.8, genre: 'Sci-Fi, Thriller',
    image: 'https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_.jpg' },
  { id: 5,  rank: 5,  title: 'Forrest Gump',             year: 1994, rating: 8.8, genre: 'Drama, Romance',
    image: 'https://m.media-amazon.com/images/M/MV5BNWIwODRlZTUtY2U3ZS00Yzg1LWJhNzYtMmZiYmEyNmU1NjMzXkEyXkFqcGdeQXVyMTQxNzMzNDI@._V1_.jpg' },
  { id: 6,  rank: 6,  title: 'The Matrix',               year: 1999, rating: 8.7, genre: 'Sci-Fi, Action',
    image: 'https://www.themoviedb.org/t/p/w500/f89U3ADr1oiB1s9GkdPOEpXUk5H.jpg' },
  { id: 7,  rank: 7,  title: 'Goodfellas',               year: 1990, rating: 8.7, genre: 'Crime, Drama',
    image: 'https://upload.wikimedia.org/wikipedia/en/7/7b/Goodfellas.jpg' },
  { id: 8,  rank: 8,  title: 'Interstellar',             year: 2014, rating: 8.7, genre: 'Sci-Fi, Drama',
    image: 'https://m.media-amazon.com/images/M/MV5BZjdkOTU3MDktN2IxOS00OGEyLWFmMjktY2FiMmZkNWIyODZiXkEyXkFqcGdeQXVyMTMxODk2OTU@._V1_.jpg' },
  { id: 9,  rank: 9,  title: 'The Silence of the Lambs', year: 1991, rating: 8.6, genre: 'Thriller, Horror',
    image: 'https://m.media-amazon.com/images/M/MV5BNjNhZTk0ZmEtNjJhMi00YzFlLWE1MmEtYzM1M2ZmMGMwMTU4XkEyXkFqcGdeQXVyNjU0OTQ0OTY@._V1_.jpg' },
  { id: 10, rank: 10, title: "Schindler's List",          year: 1993, rating: 8.9, genre: 'Drama, History',
    image: 'https://www.themoviedb.org/t/p/w500/sF1U4EUQS8YHUYjNl3pMGNIQyr0.jpg' },
])

const categoriesConPeliculas = computed(() =>
  categories.map(cat => ({
    ...cat,
    films: peliculas.value.filter(p =>
      p.genre.toLowerCase().includes(cat.name.toLowerCase())
    )
  })).filter(cat => cat.films.length > 0)
)

const verDetalles = (pelicula) => {
  alert(`🎬 ${pelicula.title} (${pelicula.year})\n⭐ ${pelicula.rating}`)
}
</script>

<template>
  <div class="app-container">

    <!-- NAVBAR -->
    <header class="navbar">
      <div class="logo-area">
        <div class="logo-icon">
          <!-- B de píxeles -->
          <svg width="22" height="26" viewBox="0 0 7 9" fill="white" xmlns="http://www.w3.org/2000/svg">
            <rect x="0" y="0" width="1" height="1"/>
            <rect x="0" y="1" width="1" height="1"/>
            <rect x="0" y="2" width="1" height="1"/>
            <rect x="0" y="3" width="1" height="1"/>
            <rect x="0" y="4" width="1" height="1"/>
            <rect x="0" y="5" width="1" height="1"/>
            <rect x="0" y="6" width="1" height="1"/>
            <rect x="0" y="7" width="1" height="1"/>
            <rect x="0" y="8" width="1" height="1"/>
            <rect x="1" y="0" width="1" height="1"/>
            <rect x="2" y="0" width="1" height="1"/>
            <rect x="3" y="0" width="1" height="1"/>
            <rect x="4" y="1" width="1" height="1"/>
            <rect x="5" y="2" width="1" height="1"/>
            <rect x="5" y="3" width="1" height="1"/>
            <rect x="4" y="4" width="1" height="1"/>
            <rect x="1" y="4" width="1" height="1"/>
            <rect x="2" y="4" width="1" height="1"/>
            <rect x="3" y="4" width="1" height="1"/>
            <rect x="5" y="5" width="1" height="1"/>
            <rect x="6" y="6" width="1" height="1"/>
            <rect x="6" y="7" width="1" height="1"/>
            <rect x="5" y="8" width="1" height="1"/>
            <rect x="1" y="8" width="1" height="1"/>
            <rect x="2" y="8" width="1" height="1"/>
            <rect x="3" y="8" width="1" height="1"/>
            <rect x="4" y="8" width="1" height="1"/>
          </svg>
        </div>
        <h1>MOVIEBAY</h1>
      </div>

      <nav class="nav-links">
        <button
          v-for="tab in tabs"
          :key="tab"
          :class="{ active: activeTab === tab }"
          @click="activeTab = tab"
        >
          {{ tab }}
        </button>
      </nav>

      <div class="user-area">
        <button class="theme-btn" title="Cambiar tema">
          {{ isDark ? '☀️' : '🌙' }}
        </button>
        <span class="user-email">👤 admin@admin.com</span>
        <button class="logout-btn">↪ Logout</button>
      </div>
    </header>

    <!-- CONTENIDO -->
    <main class="main-content">

      <TopMovies
        :peliculas="peliculas"
        @seleccionar="verDetalles"
      />

      <div class="categories-header">
        <div class="icon-box bg-orange">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
            <path d="M4 6h16M4 12h16M4 18h16" stroke="white" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </div>
        <div>
          <h2>Browse by Category</h2>
          <p>Find movies by your favorite genre</p>
        </div>
      </div>

      <MovieCategory
        v-for="cat in categoriesConPeliculas"
        :key="cat.id"
        :category="cat"
        :peliculas="cat.films"
        @seleccionar="verDetalles"
      />

    </main>
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  padding-bottom: 80px;
}

/* NAVBAR */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 32px;
  background-color: #170a30;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  flex-wrap: wrap;
  gap: 16px;
}
.logo-area { display: flex; align-items: center; gap: 12px; }
.logo-icon {
  background: linear-gradient(135deg, #a855f7, #3b82f6);
  padding: 8px 10px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo-area h1 { font-size: 1.25rem; letter-spacing: 2px; margin: 0; }
.nav-links {
  display: flex;
  background-color: #2a164d;
  border-radius: 50px;
  padding: 4px;
}
.nav-links button {
  background: transparent; border: none; color: #9ca3af;
  padding: 8px 24px; cursor: pointer; border-radius: 50px;
  transition: all 0.3s; font-size: 0.85rem;
}
.nav-links button:hover { color: white; }
.nav-links button.active {
  background-color: #1c0c3a; color: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}
.user-area { display: flex; align-items: center; gap: 16px; }
.user-email { color: #d1d5db; font-size: 0.875rem; }
.theme-btn {
  background: rgba(255,255,255,0.08);
  border: 1px solid rgba(255,255,255,0.15);
  color: white; width: 36px; height: 36px;
  border-radius: 50%; cursor: pointer; font-size: 1rem;
  display: flex; align-items: center; justify-content: center;
  transition: background 0.2s;
}
.theme-btn:hover { background: rgba(255,255,255,0.18); }
.logout-btn {
  background: transparent; border: 1px solid #4b5563; color: white;
  padding: 8px 16px; border-radius: 8px; cursor: pointer; transition: 0.3s;
}
.logout-btn:hover { background-color: rgba(255, 255, 255, 0.1); }
@media (max-width: 768px) {
  .nav-links { display: none; }
  .user-email { display: none; }
}

/* MAIN */
.main-content {
  max-width: 1280px;
  margin: 0 auto;
  padding: 32px;
}

/* CATEGORIES HEADER */
.categories-header {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 32px;
  margin-top: 48px;
}
.icon-box {
  padding: 12px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.bg-orange { background-color: #f97316; }
.categories-header h2 { font-size: 1.5rem; margin: 0; }
.categories-header p { color: #9ca3af; font-size: 0.875rem; margin-top: 4px; }
</style>