<script>
export default {
  name: 'MovieCard',
  // Recebe o objeto do filme como Propriedade (Reutilização)
  props: {
    movie: { type: Object, required: true }
  }
}
</script>

<template>
  <div class="card">
    <img :src="movie.image" :alt="movie.title" class="card-img">
    <div class="card-body">
      <h3>{{ movie.title }}</h3>
      <span class="badge">{{ movie.genre }}</span>
      <button @click="$emit('open-modal', movie)" class="btn-detail">Ver Detalhes</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  background: #1e0f24; 
  border: 1px solid #3d2349;
  border-radius: 12px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}


.card:hover { 
  transform: translateY(-5px); 
  box-shadow: 0 8px 20px rgba(208, 111, 247, 0.15);
}

.card-img { 
  width: 100%; 
  height: 260px; 
  object-fit: cover; 
}

.card-body { 
  padding: 20px; 
  display: flex; 
  flex-direction: column; 
  gap: 12px; 
}

h3 {
  font-size: 1.2rem;
  color: #ffffff;
  margin: 0;
}

.badge { 
  background: #d06ff7;
  color: #14071c;
  font-weight: bold;
  width: fit-content; 
  padding: 4px 10px; 
  border-radius: 6px; 
  font-size: 0.75rem; 
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.btn-detail { 
  background: transparent; 
  color: #d06ff7; 
  border: 2px solid #d06ff7; 
  padding: 10px; 
  font-weight: bold; 
  cursor: pointer; 
  border-radius: 6px; 
  transition: all 0.2s ease;
  margin-top: 5px;
}

.btn-detail:hover {
  background: #d06ff7;
  color: #14071c;
}
</style>