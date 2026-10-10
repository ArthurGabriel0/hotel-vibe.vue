
<script setup>
</script>

<template>
  <header class="header">
    <a href="#inicio" class="logo">Hotel<span>Vibe</span></a>

    <nav>
      <a href="#inicio">Início</a>
      <a href="#quartos">Quartos</a>
      <a href="#avaliacoes">Avaliações</a>
    </nav>

    <a href="#reservar" class="header-button">Reservar agora</a>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 22px 7%;
  background: #102b26;
  color: white;
  gap: 20px;
}

.logo {
  font-size: 25px;
  font-weight: bold;
  color: white;
  text-decoration: none;
}

.logo span {
  color: #d9b879;
}

nav {
  display: flex;
  gap: 28px;
}

nav a {
  color: #f0f0f0;
  text-decoration: none;
  font-size: 14px;
}

nav a:hover {
  color: #d9b879;
}

.header-button {
  background: #d9b879;
  color: #102b26;
  text-decoration: none;
  padding: 12px 18px;
  border-radius: 7px;
  font-weight: bold;
  font-size: 13px;
}

@media (max-width: 650px) {
  .header {
    flex-wrap: wrap;
    justify-content: center;
  }

  nav {
    gap: 14px;
  }
}
</style>
