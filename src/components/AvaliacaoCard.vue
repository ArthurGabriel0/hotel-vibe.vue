
<script setup>
defineProps({
  avaliacao: Object
})
</script>

<template>
  <article class="avaliacao">
    <div class="estrelas">★★★★★</div>

    <p class="comentario">“{{ avaliacao.comentario }}”</p>

    <div class="hospede">
      <div class="avatar">{{ avaliacao.nome.charAt(0) }}</div>

      <div>
        <strong>{{ avaliacao.nome }}</strong>
        <p>Hóspede do HotelVibe</p>
      </div>
    </div>
  </article>
</template>

<style scoped>
.avaliacao {
  background: white;
  padding: 24px;
  border-radius: 12px;
  box-shadow: 0 5px 24px #102b2610;
}

.estrelas {
  color: #bd9145;
  letter-spacing: 3px;
  font-size: 19px;
}

.comentario {
  color: #606a66;
  line-height: 1.8;
  min-height: 80px;
}

.hospede {
  display: flex;
  align-items: center;
  gap: 12px;
  border-top: 1px solid #eee;
  padding-top: 16px;
}

.avatar {
  display: grid;
  place-items: center;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  background: #e8eee9;
  color: #102b26;
  font-weight: bold;
}

.hospede strong {
  color: #102b26;
}

.hospede p {
  margin: 5px 0 0;
  color: #888;
  font-size: 12px;
}
</style>
