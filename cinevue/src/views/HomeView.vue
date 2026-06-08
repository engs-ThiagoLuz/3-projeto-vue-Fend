<script>
import MovieCard from '../components/MovieCard.vue'
import MovieModal from '../components/MovieModal.vue'

export default {
  components: { MovieCard, MovieModal },
  data() {
    return {
      searchQuery: '',
      selectedGenre: '',
      selectedMovie: null,
      isModalOpen: false,
      // Lista dinâmica de dados simulando uma API
      movies: [
        { id: 1, title: 'Inception', genre: 'Ficção', synopsis: 'Um ladrão que rouba segredos corporativos por meio do uso de tecnologia de compartilhamento de sonhos.', image: 'https://images.unsplash.com/photo-1536440136628-849c177e76a1?w=400' },
        { id: 2, title: 'The Dark Knight', genre: 'Ação', synopsis: 'Quando a ameaça conhecida como O Coringa causa estragos e caos no povo de Gotham.', image: 'https://images.unsplash.com/photo-1478760329108-5c3ed9d495a0?w=400' },
        { id: 3, title: 'Interstellar', genre: 'Ficção', synopsis: 'Uma equipe de exploradores viaja através de um buraco de minhoca no espaço na tentativa de garantir a sobrevivência da humanidade.', image: 'https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=400' },
        { id: 4, title: 'Parasite', genre: 'Drama', synopsis: 'A ganância e a discriminação de classe ameaçam a relação de simbiose recém-formada entre a rica família Park e o clã Kim.', image: 'https://images.unsplash.com/photo-1594909122845-11baa439b7bf?w=400' }
      ]
    }
  },
  computed: {
    // Filtro inteligente combinando busca por texto e gênero (Diretiva Reativa)
    filteredMovies() {
      return this.movies.filter(movie => {
        const matchesSearch = movie.title.toLowerCase().includes(this.searchQuery.toLowerCase());
        const matchesGenre = this.selectedGenre === '' || movie.genre === this.selectedGenre;
        return matchesSearch && matchesGenre;
      });
    }
  },
  methods: {
    openDetails(movie) {
      this.selectedMovie = movie;
      this.isModalOpen = true;
    }
  }
}
</script>

<template>
  <div>
    <div class="controls">
      <input v-model="searchQuery" type="text" placeholder="Buscar filme..." class="input-search">
      
      <select v-model="selectedGenre" class="select-filter">
        <option value="">Todos os Gêneros</option>
        <option value="Ficção">Ficção</option>
        <option value="Ação">Ação</option>
        <option value="Drama">Drama</option>
      </select>
    </div>

    <div class="movie-grid" v-if="filteredMovies.length > 0">
      <MovieCard 
        v-for="movie in filteredMovies" 
        :key="movie.id" 
        :movie="movie" 
        @open-modal="openDetails"
      />
    </div>
    <p v-else class="no-results">Nenhum filme encontrado.</p>

    <MovieModal 
      :movie="selectedMovie" 
      :isOpen="isModalOpen" 
      @close="isModalOpen = false"
    />
  </div>
</template>

<style scoped>
.controls { display: flex; gap: 15px; margin-bottom: 30px; flex-wrap: wrap; }
.input-search, .select-filter { padding: 10px; border-radius: 4px; border: 1px solid #444; background: #222; color: white; flex: 1; min-width: 200px; }

/* Grid Totalmente Responsivo: Mobile (1 col), Tablet (2 cols), Desktop (3+ cols) */
.movie-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 25px;
}
.no-results { text-align: center; margin-top: 40px; color: #aaa; }
</style>