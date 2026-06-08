<script>
export default {
  data() {
    return {
      // v-model atrelado aos campos
      form: { name: '', email: '', message: '' },
      errors: {},
      submitted: false
    }
  },
  methods: {
    validateForm() {
      this.errors = {};
      
      if (!this.form.name) this.errors.name = 'O nome é obrigatório.';
      if (!this.form.email) {
        this.errors.email = 'O e-mail é obrigatório.';
      } else if (!/\S+@\S+\.\S+/.test(this.form.email)) {
        this.errors.email = 'Insira um e-mail válido.';
      }
      if (this.form.message.length < 10) this.errors.message = 'A mensagem deve ter pelo menos 10 caracteres.';

      // Se não houver erros, envia
      if (Object.keys(this.errors).length === 0) {
        this.submitted = true;
        // Limpa o formulário
        this.form = { name: '', email: '', message: '' };
      }
    }
  }
}
</script>

<template>
  <div class="contact-box">
    <h2>Deixe seu Feedback</h2>
    <p>Ajude-nos a melhorar o catálogo!</p>

    <div v-if="submitted" class="success-alert">
      ✓ Feedback enviado com sucesso! Obrigado.
    </div>

    <form @submit.prevent="validateForm" novalidate>
      <div class="form-group">
        <label>Nome:</label>
        <input v-model="form.name" type="text" :class="{'input-error': errors.name}">
        <span v-if="errors.name" class="error-text">{{ errors.name }}</span>
      </div>

      <div class="form-group">
        <label>E-mail:</label>
        <input v-model="form.email" type="email" :class="{'input-error': errors.email}">
        <span v-if="errors.email" class="error-text">{{ errors.email }}</span>
      </div>

      <div class="form-group">
        <label>Sua Mensagem:</label>
        <textarea v-model="form.message" rows="4" :class="{'input-error': errors.message}"></textarea>
        <span v-if="errors.message" class="error-text">{{ errors.message }}</span>
      </div>

      <button type="submit" class="btn-submit">Enviar Avaliação</button>
    </form>
  </div>
</template>

<style scoped>
.contact-box { max-width: 600px; margin: 0 auto; background: var(--gray); padding: 30px; border-radius: 8px; }
h2 { margin-bottom: 5px; }
p { color: #aaa; margin-bottom: 20px; }
.form-group { margin-bottom: 15px; display: flex; flex-direction: column; }
label { margin-bottom: 5px; font-weight: bold; }
input, textarea { padding: 10px; background: #111; border: 1px solid #444; color: white; border-radius: 4px; }
.input-error { border-color: var(--primary); }
.error-text { color: var(--primary); font-size: 0.85rem; margin-top: 5px; }
.btn-submit { background: var(--primary); color: white; border: none; padding: 12px; font-weight: bold; cursor: pointer; border-radius: 4px; margin-top: 10px; }
.success-alert { background: #2e7d32; color: white; padding: 15px; border-radius: 4px; margin-bottom: 20px; }
</style>