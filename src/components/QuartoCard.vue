
<script setup>
defineProps({
  quarto: Object
})

defineEmits(['reservar'])
</script>

<template>
  <article class="quarto-card">
    <img :src="quarto.imagem" :alt="quarto.nome">

    <div class="conteudo">
      <span class="categoria">{{ quarto.categoria }}</span>
      <h3>{{ quarto.nome }}</h3>
      <p>{{ quarto.descricao }}</p>

      <div class="detalhes">
        <span>♙ {{ quarto.hospedes }} hóspedes</span>
        <span>Wi-Fi grátis</span>
      </div>

      <div class="rodape">
        <div>
          <strong>R$ {{ quarto.preco }}</strong>
          <small>/ diária</small>
        </div>

        <button @click="$emit('reservar', quarto)">
          Reservar
        </button>
      </div>
    </div>
  </article>
</template>

<style scoped>
.quarto-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 5px 24px #102b2610;
  transition: transform 0.2s;
}

.quarto-card:hover {
  transform: translateY(-5px);
}

.quarto-card img {
  width: 100%;
  height: 210px;
  object-fit: cover;
}

.conteudo {
  padding: 22px;
}

.categoria {
  color: #9c7a3b;
  font-size: 12px;
  text-transform: uppercase;
  font-weight: bold;
  letter-spacing: 1px;
}

h3 {
  color: #102b26;
  font-size: 22px;
  margin: 10px 0;
}

.conteudo p {
  color: #777;
  line-height: 1.6;
  font-size: 14px;
  min-height: 45px;
}

.detalhes {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  font-size: 12px;
  color: #666;
  margin: 18px 0;
}

.rodape {
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-top: 1px solid #eee;
  padding-top: 18px;
}

.rodape strong {
  color: #102b26;
  font-size: 22px;
}

.rodape small {
  color: #777;
}

button {
  background: #102b26;
  color: white;
  border: none;
  border-radius: 6px;
  padding: 12px 16px;
  cursor: pointer;
}

button:hover {
  background: #244a40;
}
</style>
