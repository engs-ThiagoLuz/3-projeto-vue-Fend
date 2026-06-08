<script>
export default {
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
  background: var(--gray);
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.2s;
}
.card:hover { transform: scale(1.03); }
.card-img { width: 100%; height: 250px; object-fit: cover; }
.card-body { padding: 15px; display: flex; flex-direction: column; gap: 10px; }
.badge { background: var(--primary); width: fit-content; padding: 3px 8px; border-radius: 4px; font-size: 0.8rem; }
.btn-detail { background: #fff; color: #000; border: none; padding: 8px; font-weight: bold; cursor: pointer; border-radius: 4px; }
</style>