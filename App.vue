<template>
  <div class="container">
    <img src="./assets/logo.png" alt="Logo" width="100" />
    <h1>Calculadora Aritmética</h1>
    
    <div class="inputs">
      <input type="number" v-model.number="numero1" placeholder="Número 1" />
      <select v-model="operacao">
        <option value="+">Soma (+)</option>
        <option value="-">Subtração (-)</option>
        <option value="*">Multiplicação (*)</option>
        <option value="/">Divisão (/)</option>
      </select>
      <input type="number" v-model.number="numero2" placeholder="Número 2" />
    </div>

    <div class="resultado">
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const numero1 = ref(0)
const numero2 = ref(0)
const operacao = ref('+')

const resultado = computed(() => {
  switch (operacao.value) {
    case '+': return numero1.value + numero2.value
    case '-': return numero1.value - numero2.value
    case '*': return numero1.value * numero2.value
    case '/': return numero2.value !== 0 ? numero1.value / numero2.value : 'Erro: divisão por zero'
    default: return 'Operação inválida'
  }
})
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 50px auto;
  padding: 2rem;
  text-align: center;
  border: 1px solid #ccc;
  border-radius: 8px;
}
.inputs {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 1rem;
}
input, select {
  padding: 0.5rem;
  font-size: 1rem;
}
.resultado {
  font-size: 1.2rem;
  font-weight: bold;
}
</style>
