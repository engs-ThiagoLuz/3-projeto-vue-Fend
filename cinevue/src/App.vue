<template>
  <header class="navbar">
    <div class="nav-container">
      <h1 class="logo">CineVue</h1>
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
  background-color: #000;
  padding: 15px 0;
  border-bottom: 2px solid var(--primary);
}
.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}
.logo { color: var(--primary); }
nav a {
  color: white;
  text-decoration: none;
  margin-left: 20px;
  font-weight: bold;
}
nav a.router-link-exact-active {
  color: var(--primary);
}
</style>