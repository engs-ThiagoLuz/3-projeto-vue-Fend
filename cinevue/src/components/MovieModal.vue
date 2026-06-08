<script>
export default {
  props: {
    movie: Object,
    isOpen: Boolean
  }
}
</script>

<template>
  <div v-if="isOpen" class="modal-overlay" @click.self="$emit('close')">
    <div class="modal-content">
      <h2>{{ movie.title }}</h2>
      <p class="genre"><strong>Gênero:</strong> {{ movie.genre }}</p>
      <p class="synopsis">{{ movie.synopsis }}</p>
      <button @click="$emit('close')" class="btn-close">Fechar</button>
    </div>
  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed; top: 0; left: 0; width: 100%; height: 100%;
  background: rgba(0,0,0,0.8); display: flex; align-items: center; justify-content: center; z-index: 100;
}
.modal-content {
  background: var(--gray); padding: 30px; border-radius: 8px; max-width: 500px; width: 90%;
}
.genre { color: var(--primary); margin: 10px 0; }
.synopsis { margin-bottom: 20px; line-height: 1.5; }
.btn-close { background: var(--primary); color: white; border: none; padding: 10px 20px; cursor: pointer; border-radius: 4px; }
</style>