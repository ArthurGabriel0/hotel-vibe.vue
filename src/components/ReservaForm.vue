
<script setup>
import { ref } from 'vue'

const props = defineProps({
  quartoSelecionado: Object
})

const emit = defineEmits(['confirmar'])

const nome = ref('')
const entrada = ref('')
const saida = ref('')
const hospedes = ref(1)
const erro = ref('')

function enviarReserva() {
  erro.value = ''

  if (!nome.value.trim() || !entrada.value || !saida.value) {
    erro.value = 'Preencha todos os campos.'
    return
  }

  if (saida.value <= entrada.value) {
    erro.value = 'A saída deve ser depois da entrada.'
    return
  }

  if (!props.quartoSelecionado) {
    erro.value = 'Selecione um quarto antes de reservar.'
    return
  }

  const inicio = new Date(entrada.value + 'T12:00:00')
  const fim = new Date(saida.value + 'T12:00:00')
  const diarias = Math.round((fim - inicio) / 86400000)

  emit('confirmar', {
    nome: nome.value,
    entrada: entrada.value,
    saida: saida.value,
    hospedes: hospedes.value,
    quarto: props.quartoSelecionado.nome,
    preco: props.quartoSelecionado.preco,
    diarias: diarias,
    total: diarias * props.quartoSelecionado.preco
  })
}
</script>

<template>
  <form class="formulario" @submit.prevent="enviarReserva">
    <label>Nome completo</label>
    <input v-model="nome" type="text" placeholder="Digite seu nome">

    <label>Quarto escolhido</label>
    <input
      :value="quartoSelecionado ? quartoSelecionado.nome : 'Selecione um quarto acima'"
      type="text"
      readonly
    >

    <div class="datas">
      <div>
        <label>Check-in</label>
        <input v-model="entrada" type="date">
      </div>

      <div>
        <label>Check-out</label>
        <input v-model="saida" type="date" :min="entrada || undefined">
      </div>
    </div>

    <label>Quantidade de hóspedes</label>
    <select v-model="hospedes">
      <option :value="1">1 hóspede</option>
      <option :value="2">2 hóspedes</option>
      <option :value="3">3 hóspedes</option>
      <option :value="4">4 hóspedes</option>
    </select>

    <p v-if="erro" class="erro">{{ erro }}</p>

    <button type="submit">Confirmar reserva</button>
  </form>
</template>

<style scoped>
.formulario {
  display: flex;
  flex-direction: column;
  gap: 10px;
  background: white;
  padding: 28px;
  border-radius: 12px;
  box-shadow: 0 5px 25px #102b2610;
}

label {
  font-size: 13px;
  font-weight: bold;
  color: #102b26;
  margin-top: 8px;
}

input, select {
  width: 100%;
  box-sizing: border-box;
  padding: 13px;
  border: 1px solid #ddd;
  border-radius: 6px;
  background: white;
  font: inherit;
}

.datas {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.datas > div {
  min-width: 0;
}

button {
  margin-top: 12px;
  padding: 15px;
  border: none;
  border-radius: 6px;
  background: #102b26;
  color: white;
  font-weight: bold;
  cursor: pointer;
}

.erro {
  color: #b42318;
  font-size: 13px;
}

@media (max-width: 450px) {
  .datas {
    grid-template-columns: 1fr;
  }
}
</style>
