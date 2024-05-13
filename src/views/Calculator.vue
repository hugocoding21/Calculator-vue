<template>
  <div class="calculator">
    <img
      @click="resetResult"
      id="image"
      alt="Vue logo"
      class="logo"
      src="@/assets/logo.svg"
      width="125"
      height="125" />
    <input type="text" v-model="result" readonly />
    <div>
      <button @click="appendToResult('7')">7</button>
      <button @click="appendToResult('8')">8</button>
      <button @click="appendToResult('9')">9</button>
      <button @click="appendToResult('/')">/</button>
    </div>
    <div>
      <button @click="appendToResult('4')">4</button>
      <button @click="appendToResult('5')">5</button>
      <button @click="appendToResult('6')">6</button>
      <button @click="appendToResult('*')">*</button>
    </div>
    <div>
      <button @click="appendToResult('1')">1</button>
      <button @click="appendToResult('2')">2</button>
      <button @click="appendToResult('3')">3</button>
      <button @click="appendToResult('-')">-</button>
    </div>
    <div>
      <button @click="appendToResult('.')">.</button>
      <button @click="appendToResult('0')">0</button>
      <button @click="calculate()">=</button>
      <button @click="appendToResult('+')">+</button>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      result: "",
    };
  },

  methods: {
    appendToResult(value): void {
      this.result += value;
    },

    calculate(): string {
      try {
        this.result = eval(this.result);
      } catch (e) {
        this.handleError();
      }
    },

    handleError(): string {
      this.result = "Erreur";
      setTimeout(() => {
        this.result = "";
      }, 1000);
    },

    resetResult(): string {
      this.result = "";
    },
  },
};
</script>

<style>
* {
  font-weight: 700;
  font-size: 18px;
}
#image {
  height: 3rem;
}
.calculator {
  display: flex;
  flex-direction: column;
  padding: 1rem;
  border: 2px solid rgb(0, 0, 0);
  border-radius: 20px;
  align-items: center;
  background-color: rgb(74, 128, 168);
}
input {
  border: 2px solid rgb(0, 0, 0);
  outline: none;
  text-align: right;
  border-radius: 5px;
  width: 90%;
  height: 2rem;
  margin-bottom: 2rem;
  margin-top: 2rem;
}
button {
  border-radius: 5px;
  border: 2px solid rgb(0, 0, 0);
  margin: 2px;
  width: 4rem;
  height: 3rem;
}
button :hover {
  background-color: #000;
}
</style>
