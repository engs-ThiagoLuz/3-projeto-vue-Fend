<script>
export default {
  name: 'MovieModal',
  props: {
    movie: Object,
    isOpen: Boolean
  }
}
</script>

<template>
  <div v-if="isOpen && movie" class="modal-overlay" @click.self="$emit('close')">
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
  background: rgba(12, 5, 15, 0.85); /* Fundo escuro transparente */
  backdrop-filter: blur(8px); 
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 999;
  padding: 20px;
}

.modal-content {
  background: rgb(208, 111, 247); /* O rosa agradável principal */
  color: #14071c; /* Texto escuro para excelente legibilidade sobre o rosa */
  padding: 35px;
  border-radius: 16px;
  max-width: 500px;
  width: 100%;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
  animation: fadeIn 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

h2 {
  font-size: 1.8rem;
  margin-bottom: 8px;
  color: #14071c;
  font-weight: 800;
}

.genre {
  color: #5b0ca3; /* Roxo escuro para destacar o rótulo do gênero */
  font-weight: 700;
  margin-bottom: 18px;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 0.5px;
}

.synopsis {
  color: #2c163a;
  line-height: 1.6;
  margin-bottom: 25px;
  font-size: 1rem;
}

.btn-close {
  background: #14071c; /* Botão escuro contratando com o fundo rosa */
  color: #ffffff;
  border: none;
  padding: 12px 28px;
  font-weight: bold;
  font-size: 1rem;
  cursor: pointer;
  border-radius: 8px;
  transition: background 0.2s, transform 0.1s;
  width: 100%;
}

.btn-close:hover {
  background: #2a113b;
}

.btn-close:active {
  transform: scale(0.98);
}

@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.95); }
  to { opacity: 1; transform: scale(1); }
}
</style>