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
  background-color: rgb(208, 111, 247);
  backdrop-filter: blur(10px);
  position: sticky;
  top: 0;
  z-index: 100;
  padding: 20px 0;
  border-bottom: 1px solid var(--border-color);
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
  color: var(--primary);
  font-size: 1.8rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

nav {
  display: flex;
  gap: 25px;
}

nav a {
  color: var(--text-muted);
  text-decoration: none;
  font-weight: 600;
  font-size: 1rem;
  transition: color 0.2s;
}

nav a:hover {
  color: #fff;
}

nav a.router-link-exact-active {
  color: var(--primary);
}
</style>