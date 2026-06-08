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
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.75);
  backdrop-filter: blur(8px); /* Desfoca os cards atrás */
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 999;
  padding: 20px;
}

.modal-content {
  background: rgb(208, 111, 247);
  color: var(--text-main); 
  padding: 40px;
  border-radius: 12px;
  max-width: 550px;
  width: 100%;
  border: 1px solid var(--border-color);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
  animation: fadeIn 0.3s ease;
}

h2 {
  font-size: 2rem;
  margin-bottom: 10px;
  color: #fff;
}

.genre {
  color: var(--primary);
  font-weight: 600;
  margin-bottom: 20px;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 1px;
}

.synopsis {
  color: var(--text-muted);
  line-height: 1.6;
  margin-bottom: 30px;
  font-size: 1rem;
}

.btn-close {
  background: var(--primary);
  color: white;
  border-color: red;
  padding: 12px 28px;
  font-weight: bold;
  font-size: 1rem;
  cursor: pointer;
  border-radius: 6px;
  transition: background 0.2s;
  width: 100%;
}

.btn-close:hover {
  background: #b80710;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>