<template>
  <div class="calculator">
    <h1>Calculadora Aritmética</h1>
    <div class="inputs">
      <input 
        type="number" 
        v-model="number1" 
        placeholder="Primeiro número"
        @input="calculate"
      >
      <select v-model="operation" @change="calculate">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">×</option>
        <option value="/">÷</option>
      </select>
      <input 
        type="number" 
        v-model="number2" 
        placeholder="Segundo número"
        @input="calculate"
      >
    </div>
    <div class="result">
      <h2>Resultado: {{ result }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      number1: '',
      number2: '',
      operation: '+',
      result: 0
    }
  },
  methods: {
    calculate() {
      const num1 = parseFloat(this.number1) || 0;
      const num2 = parseFloat(this.number2) || 0;
      
      switch(this.operation) {
        case '+':
          this.result = num1 + num2;
          break;
        case '-':
          this.result = num1 - num2;
          break;
        case '*':
          this.result = num1 * num2;
          break;
        case '/':
          this.result = num2 !== 0 ? num1 / num2 : 'Erro: Divisão por zero';
          break;
        default:
          this.result = 0;
      }
    }
  }
}
</script>

<style>
.calculator {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
}

h1 {
  color: #2c3e50;
  margin-bottom: 30px;
}

.inputs {
  display: flex;
  gap: 10px;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

input, select {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

select {
  width: 60px;
  text-align: center;
}

.result {
  margin-top: 20px;
  padding: 15px;
  background-color: #f8f9fa;
  border-radius: 4px;
}

h2 {
  color: #2c3e50;
  margin: 0;
}
</style> 