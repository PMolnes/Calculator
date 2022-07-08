<template>
  <div class="drop-shadow-2xl flex flex-col items-center justify-center max-w-sm h-96">
    <div class="flex flex-col items-end justify-between w-96 h-32">
      <div class="flex flex-col items-end justify-between bg-[#82a3a2] w-96 h-32 p-4 border border-grey">
        <div class="text-white text-opacity-75" :class="textSize(previousOperand)">
          {{ previousOperand }}
        </div>
        <div class="max-w-full text-white font-bold" :class="textSize(currentOperand)">{{ currentOperand }}</div>
      </div>
    </div>
    <div class="grid grid-cols-4 w-full h-full bg-white">
      <CalculatorButton @click="allClear" class="col-span-2"
        >AC</CalculatorButton
      >
      <CalculatorButton @click="clear">C</CalculatorButton>
      <CalculatorButton @click="operation" value="/">&#247;</CalculatorButton>
      <CalculatorButton @click="addOperand" value="7">7</CalculatorButton>
      <CalculatorButton @click="addOperand" value="8">8</CalculatorButton>
      <CalculatorButton @click="addOperand" value="9">9</CalculatorButton>
      <CalculatorButton @click="operation" value="*">&times;</CalculatorButton>
      <CalculatorButton @click="addOperand" value="4">4</CalculatorButton>
      <CalculatorButton @click="addOperand" value="5">5</CalculatorButton>
      <CalculatorButton @click="addOperand" value="6">6</CalculatorButton>
      <CalculatorButton @click="operation" value="-">&minus;</CalculatorButton>
      <CalculatorButton @click="addOperand" value="1">1</CalculatorButton>
      <CalculatorButton @click="addOperand" value="2">2</CalculatorButton>
      <CalculatorButton @click="addOperand" value="3">3</CalculatorButton>
      <CalculatorButton @click="operation" value="+">&plus;</CalculatorButton>
      <CalculatorButton @click="addOperand" value="0">0</CalculatorButton>
      <CalculatorButton @click="addOperand" value=".">.</CalculatorButton>
      <CalculatorButton @click="equate" class="col-span-2" value="=">=</CalculatorButton>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref, type Ref } from "vue";
import CalculatorButton from "./CalculatorButton.vue";

const currentOperand = ref("");
const previousOperand = ref("");
const expression = ref("");

const textSize = (operand: string) => {
  return operand.length > 9 ? "text-2xl" : "text-4xl";
};

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
  if (currentOperand.value !== "" && currentOperand.value[currentOperand.value.length - 1] === " ") {
    currentOperand.value = currentOperand.value.slice(0, -2);
    expression.value = expression.value.slice(0, -2);
  } else if (currentOperand.value !== "") {
    currentOperand.value = currentOperand.value.slice(0, -1);
    expression.value = expression.value.slice(0, -1);
  }
};

const operation = (event: Event) => {
  expression.value += (<HTMLInputElement>event.target).value;
  currentOperand.value = currentOperand.value +=
    " " + (<HTMLInputElement>event.target).innerText + " ";
};

const equate = () => {
  previousOperand.value = currentOperand.value;
  if (eval(expression.value).toString().length > 10) {
    currentOperand.value = eval(expression.value).toExponential(2);
  } else {
    currentOperand.value = eval(expression.value);
  }
  expression.value = currentOperand.value;
};
</script>
