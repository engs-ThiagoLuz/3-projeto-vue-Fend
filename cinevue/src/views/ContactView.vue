<script>
export default {
  name: 'ContactView',
  data() {
    return {
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

      if (Object.keys(this.errors).length === 0) {
        this.submitted = true;
        this.form = { name: '', email: '', message: '' };
        // Remove o alerta de sucesso após alguns segundos
        setTimeout(() => { this.submitted = false; }, 5000);
      }
    }
  }
}
</script>

<template>
  <div class="contact-box">
    <h2>Deixe seu Feedback</h2>
    <p class="subtitle">Ajude-nos a melhorar o catálogo!</p>

    <div v-if="submitted" class="success-alert">
      ✓ Feedback enviado com sucesso! Obrigado.
    </div>

    <form @submit.prevent="validateForm" novalidate>
      <div class="form-group">
        <label>Nome:</label>
        <input v-model="form.name" type="text" :class="{'input-error': errors.name}" placeholder="Seu nome">
        <span v-if="errors.name" class="error-text">{{ errors.name }}</span>
      </div>

      <div class="form-group">
        <label>E-mail:</label>
        <input v-model="form.email" type="email" :class="{'input-error': errors.email}" placeholder="seu@email.com">
        <span v-if="errors.email" class="error-text">{{ errors.email }}</span>
      </div>

      <div class="form-group">
        <label>Sua Mensagem:</label>
        <textarea v-model="form.message" rows="4" :class="{'input-error': errors.message}" placeholder="Escreva aqui sua opinião..."></textarea>
        <span v-if="errors.message" class="error-text">{{ errors.message }}</span>
      </div>

      <button type="submit" class="btn-submit">Enviar Avaliação</button>
    </form>
  </div>
</template>

<style scoped>
.contact-box { 
  max-width: 550px; 
  margin: 40px auto; 
  background: #1e0f24; 
  border: 1px solid #3d2349;
  padding: 35px; 
  border-radius: 12px; 
}

h2 { margin-bottom: 5px; color: #fff; }
.subtitle { color: #bda6c7; margin-bottom: 25px; font-size: 0.95rem; }

.form-group { margin-bottom: 20px; display: flex; flex-direction: column; }
label { margin-bottom: 8px; font-weight: 600; color: #e0d5e6; font-size: 0.9rem; }

/* Input padronizado com a cor que você definiu na Home */
input, textarea { 
  padding: 12px 16px; 
  background: rgb(36, 19, 43); 
  border: 1px solid #4a2c57; 
  color: white; 
  border-radius: 8px; 
  font-size: 1rem;
  transition: all 0.3s ease;
}

input:focus, textarea:focus {
  outline: none;
  border-color: rgb(208, 111, 247);
  box-shadow: 0 0 0 3px rgba(208, 111, 247, 0.2);
}

/* Erros visuais elegantes em tom rosa/avermelhado condizente */
.input-error { border-color: #ff527b !important; }
.error-text { color: #ff527b; font-size: 0.8rem; margin-top: 6px; font-weight: 500; }

.btn-submit { 
  background: rgb(208, 111, 247); 
  color: #14071c; 
  padding: 14px; 
  font-weight: bold; 
  font-size: 1rem;
  cursor: pointer; 
  border-radius: 8px; 
  border: none;
  margin-top: 10px; 
  width: 100%;
  transition: background 0.2s;
}

.btn-submit:hover { 
  background: #be5ce7; 
}

.success-alert { 
  background: #1b4d22; 
  color: #c8e6c9; 
  border: 1px solid #2e7d32;
  padding: 12px; 
  border-radius: 6px; 
  margin-bottom: 20px; 
  font-size: 0.95rem;
  text-align: center;
}
</style>