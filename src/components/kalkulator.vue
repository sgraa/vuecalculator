<template>
  <div id="app">
      <input v-model="result" placeholder="kalkulatorrrrr" type="text" class="input">
      <input v-model="hasil" type="text" class="result" readonly>
      <div class="keys">
          <button class="operator font-sans" @click="clearResult">C</button>
          <button class="operator" @click="backspace">CE</button>
          <button class="operator">😎</button>
          <button class="operator" @click="addToResult('/')">/</button>
          <button @click="addToResult('1')">1</button>
          <button @click="addToResult('2')">2</button>
          <button @click="addToResult('3')">3</button>
          <button class="operator" @click="addToResult('*')">*</button>
          <button @click="addToResult('4')">4</button>
          <button @click="addToResult('5')">5</button>
          <button @click="addToResult('6')">6</button>
          <button class="operator" @click="addToResult('-')">-</button>
          <button @click="addToResult('7')">7</button>
          <button @click="addToResult('8')">8</button>
          <button @click="addToResult('9')">9</button>
          <button class="operator" @click="addToResult('+')">+</button>
          <button @click="addToResult('0')">0</button>
          <button @click="addToResult('.')">.</button>
          <button class="equal-sign operator" @click="calculate">=</button>
      </div>
  </div>
</template>

<script>
export default {
  data() {
      return {
          result: '',
          hasil: ''
      };
  },
  methods: {
      addToResult(value) {
          this.result += value;
      },
      clearResult() {
          this.result = '';
      },
      backspace() {
          this.result = this.result.slice(0, -1);
      },
      calculate() {
          try {
              this.hasil = eval(this.result);
              this.result = '';
          } catch (error) {
              this.hasil = 'Error';
              this.result = '';
          }
      }
  }
};
</script>

<style scoped>
#app {
  width: 500px; /* Lebar kalkulator */
  margin: 0 auto;
  background-color: #231a1a; /* Warna latar belakang */
  padding: 30px;
  border-radius: 10px; /* Tampilan sudut melengkung */
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2); /* Efek bayangan */
}

.input {
  color:#a37474;
  width: 90%;
  padding: 10px;
  margin-right: 50px;
  margin-bottom: 10px;
  font-size: 18px; /* Ukuran font yang lebih besar */
  border: none;
  border-radius: 5px;
}

.result {
  color:#a37474;
  width: 70%;
  padding: 10px;
  margin-left: 20px;
  margin-bottom: 10px;
  font-size: 18px; /* Ukuran font yang lebih besar */
  border: none;
  border-radius: 5px;
}

.keys {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px; /* Jarak antara tombol */
}

.operator {
  background-color: #a37474; /* Warna latar belakang tombol operator */
  border: none;
  border-radius: 5px;
  font-size: 20px;
  cursor: pointer;
  transition: background-color 0.2s; /* Efek hover */
}

.operator:hover {
  background-color: #ff6600;
}

.equal-sign {
  grid-column: span 2;
  background-color: #ff6600; /* Warna latar belakang tombol sama dengan */
  color: #231a1a; /* Warna teks tombol sama dengan */
  border: none;
  border-radius: 5px;
  font-size: 20px;
  cursor: pointer;
  transition: background-color 0.2s; /* Efek hover */
}

.equal-sign:hover {
  background-color: #231a1a; /* Warna latar belakang saat tombol dihover */
}
</style>
