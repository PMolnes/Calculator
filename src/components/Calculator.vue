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
      <button @click="operation" value="&#247;">&#247;</button>
      <button @click="addOperand" value="7">7</button>
      <button @click="addOperand" value="8">8</button>
      <button @click="addOperand" value="9">9</button>
      <button @click="operation" value="&times;">&times;</button>
      <button @click="addOperand" value="4">4</button>
      <button @click="addOperand" value="5">5</button>
      <button @click="addOperand" value="6">6</button>
      <button @click="operation" value="+">+</button>
      <button @click="addOperand" value="1">1</button>
      <button @click="addOperand" value="2">2</button>
      <button @click="addOperand" value="3">3</button>
      <button @click="operation" value="-">-</button>
      <button @click="addOperand" value="0">0</button>
      <button @click="addOperand" value=".">.</button>
      <button @click="equate" class="double">=</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const currentOperand = ref("");
const previousOperand = ref("");
const expression = ref("");
const map = new Map([
  ["+", (a: number, b: number) => a + b],
  ["-", (a: number, b: number) => a - b],
  ["×", (a: number, b: number) => a * b],
  ["÷", (a: number, b: number) => a / b],
]);

const addOperand = (event: Event) => {
  expression.value += (<HTMLInputElement>event.target).value;
  currentOperand.value += (<HTMLInputElement>event.target).value;
};

const allClear = () => {
  currentOperand.value = "";
  previousOperand.value = "";
  expression.value = "";
};

const clear = () => {
  if (currentOperand.value !== '') {
    currentOperand.value = currentOperand.value.slice(0, -1);
    expression.value = currentOperand.value.slice(0, -1);
  }
};

const operation = (event: Event) => {
  expression.value += (<HTMLInputElement>event.target).value;
  previousOperand.value = currentOperand.value += " " + (<HTMLInputElement>event.target).value;
  currentOperand.value = "";
};

const equate = () => {
  console.log(expression.value);
  const numA = parseFloat(
    previousOperand.value.split(" ").values().next().value
  );
  const numB = parseFloat(currentOperand.value);
  const operator = previousOperand.value.split(" ")[1];
  if (isNaN(numA) || isNaN(numB)) {
    currentOperand.value = "ERROR";
    previousOperand.value = "";
  } else {
    previousOperand.value = previousOperand.value += " " + currentOperand.value;
    currentOperand.value = "" + map.get(operator)?.(numA, numB);
  }
};
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
  max-width: 100%;
  height: 100%;
}

.previous-operand {
  font-size: 2rem;
  color: rgb(255, 255, 255);
  opacity: 0.75;
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
