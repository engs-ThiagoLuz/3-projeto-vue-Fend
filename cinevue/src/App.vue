<template>
  <header class="navbar">
    <div class="nav-container">
      <h1 class="logo">CineVue - Filmes para todos e todes!</h1>
      <nav>
        <router-link to="/">Início</router-link>
        <router-link to="/contato">Feedback</router-link>
      </nav>
    </div>
  </header>

  <main class="container">
    <router-view />
  </main>
</template>

<style scoped>
.navbar {
  /* Tom roxo escuro com os inputs */
  background-color: rgba(36, 19, 43, 0.85); 
  
  /* Efeito glassmorphism para rolar a página */
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  
  position: sticky;
  top: 0;
  z-index: 100;
  padding: 14px 0; 
  
  /* Linha divisória usando o rosa de destaque */
  border-bottom: 2px solid rgb(208, 111, 247);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  color: rgb(208, 111, 247); 
  font-size: 1.4rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

nav {
  display: flex;
  gap: 15px;
}

nav a {
  color: #e0d5e6; 
  text-decoration: none;
  font-weight: 600;
  font-size: 0.95rem;
  padding: 8px 16px;
  border-radius: 6px;
  transition: all 0.2s ease;
}

nav a:hover {
  color: #ffffff;
  background-color: rgba(208, 111, 247, 0.1); 
}

nav a.router-link-exact-active {
  /* Contraste escuro para leitura sobre o fundo rosa do link ativo */
  color: #14071c; 
  background-color: rgb(208, 111, 247);
  font-weight: 700;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 0;
}

/* Alinhamento empilhado automático para dispositivos móveis */
@media (max-width: 768px) {
  .nav-container {
    flex-direction: column;
    gap: 12px;
    text-align: center;
  }
  .logo {
    font-size: 1.2rem;
  }
  nav {
    width: 100%;
    justify-content: center;
    gap: 10px;
  }
  nav a {
    padding: 6px 12px;
    font-size: 0.9rem;
  }
}
</style>