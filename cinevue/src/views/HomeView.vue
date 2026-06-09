<script>
import MovieCard from '../components/MovieCard.vue'
import MovieModal from '../components/MovieModal.vue'

export default {
  name: 'HomeView',
  components: { MovieCard, MovieModal },
  data() {
    return {
      searchQuery: '',
      selectedGenre: '',
      selectedMovie: null,
      isModalOpen: false,
      movies: [
        { id: 1, title: 'Inception', genre: 'Ficção', synopsis: 'Um ladrão que rouba segredos corporativos por meio do uso de tecnologia de compartilhamento de sonhos.', image: 'https://images.unsplash.com/photo-1536440136628-849c177e76a1?w=400' },
        { id: 2, title: 'The Dark Knight', genre: 'Ação', synopsis: 'Quando a ameaça conhecida como O Coringa causa estragos e caos no povo de Gotham.', image: 'https://images.unsplash.com/photo-1478760329108-5c3ed9d495a0?w=400' },
        { id: 3, title: 'Interstellar', genre: 'Ficção', synopsis: 'Uma equipe de exploradores viaja através de um buraco de minhoca no espaço na tentativa de garantir a sobrevivência da humanidade.', image: 'https://images.unsplash.com/photo-1451187580459-43490279c0fa?w=400' },
        { id: 4, title: 'Parasite', genre: 'Drama', synopsis: 'A ganância e a discriminação de classe ameaçam a relação de simbiose recém-formada entre a rica família Park e o clã Kim.', image: 'https://images.unsplash.com/photo-1594909122845-11baa439b7bf?w=400' }
      ]
    }
  },
  computed: {
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
  <div class="home-page">
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
    <p v-else class="no-results">Nenhum filme encontrado para a sua busca.</p>

    <MovieModal 
      :movie="selectedMovie" 
      :isOpen="isModalOpen" 
      @close="isModalOpen = false"
    />
  </div>
</template>

<style scoped>
.home-page {
  padding: 20px 0;
}

.controls {
  display: flex;
  gap: 20px;
  margin-bottom: 40px;
}

.input-search, .select-filter {
  padding: 14px 20px;
  border-radius: 8px;
  border: 1px solid #3d2349;
  background: rgb(36, 19, 43); /* Sua escolha excelente de cor */
  color: #ffffff; 
  font-size: 1rem;
  transition: all 0.3s ease;
}

.input-search {
  flex: 2;
}

.select-filter {
  flex: 1;
  cursor: pointer;
}

.input-search:focus, .select-filter:focus {
  outline: none;
  border-color: rgb(208, 111, 247);
  box-shadow: 0 0 0 3px rgba(208, 111, 247, 0.2);
}

/* Grid Responsiva e fluida com CSS nativo puro */
.movie-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 30px;
}

.no-results {
  color: #bda6c7;
  text-align: center;
  font-size: 1.1rem;
  margin-top: 50px;
}

/* Ajustes de responsividade para celulares */
@media (max-width: 768px) {
  .controls {
    flex-direction: column;
    gap: 15px;
  }
  .input-search, .select-filter {
    width: 100%;
  }
}
</style>