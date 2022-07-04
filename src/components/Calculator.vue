<template>
  <div class="calculator">
    <div class="output">
      <div class="operands">
        <div class="previous-operand">{{ previousOperand }}</div>
        <div class="current-operand">{{ currentOperand }}</div>
      </div>
    </div>
    <div class="buttons">
      <button @click="allClear" class="double">AC</button>
      <button @click="clear">C</button>
      <button @click="addOperand" value="&#247;">&#247;</button>
      <button @click="addOperand" value="7">7</button>
      <button @click="addOperand" value="8">8</button>
      <button @click="addOperand" value="9">9</button>
      <button>&times;</button>
      <button @click="addOperand" value="4">4</button>
      <button @click="addOperand" value="5">5</button>
      <button @click="addOperand" value="6">6</button>
      <button>+</button>
      <button @click="addOperand" value="1">1</button>
      <button @click="addOperand" value="2">2</button>
      <button @click="addOperand" value="3">3</button>
      <button>-</button>
      <button @click="addOperand" value="0">0</button>
      <button>.</button>
      <button class="double">=</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const currentOperand = ref("");
const previousOperand = ref("");

const addOperand = (event: Event) => {
  if ((<HTMLInputElement>event.target).value === "&#247;") {
    previousOperand.value = currentOperand.value;
  }
  currentOperand.value += (<HTMLInputElement>event.target).value;
  console.log(currentOperand.value);
};

const allClear = () => {
  currentOperand.value = "";
};

const clear = () => {
  currentOperand.value = currentOperand.value.slice(0, -1);
};

const divide = (a: string, b: string) => {};
</script>

<style scoped>
.calculator {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
}

.output {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: space-between;
  background-color: rgb(88, 134, 218);
  width: 25rem;
  height: 8rem;
}

.operands {
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: space-between;
  width: 100%;
  height: 100%;
}

.previous-operand {
  font-size: 2rem;
  color: white;
}

.current-operand {
  font-size: 2rem;
  color: white;
  font-weight: bold;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  width: 25rem;
  height: 25rem;
}

button {
  font-size: 3rem;
}

.double {
  grid-column: span 2;
}
</style>
