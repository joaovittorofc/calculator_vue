<template>
  <div class="container">
    <h1>Calculadora Aritmética</h1>
    <div class="inputs">
      <input type="number" v-model.number="num1" placeholder="Número 1" />
      <select v-model="operacao">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input type="number" v-model.number="num2" placeholder="Número 2" />
    </div>
    <div class="resultado">
      <h2>Resultado: {{ resultado }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operacao: '+'
    }
  },
  computed: {
    resultado() {
      const { num1, num2, operacao } = this
      if (operacao === '+') return num1 + num2
      if (operacao === '-') return num1 - num2
      if (operacao === '*') return num1 * num2
      if (operacao === '/') return num2 !== 0 ? (num1 / num2).toFixed(2) : 'Erro'
      return 0
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 40px auto;
  text-align: center;
  font-family: Arial, sans-serif;
}
.inputs {
  display: flex;
  gap: 10px;
  justify-content: center;
  margin: 20px 0;
}
input,
select {
  padding: 8px;
  font-size: 16px;
}
.resultado h2 {
  color: #2c3e50;
}
</style>
