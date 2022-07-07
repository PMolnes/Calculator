<script setup lang="ts">
import Calculator from "./components/Calculator.vue";
</script>

<template>
  <Calculator />
</template>

<script setup lang="ts"></script>

<style>
@font-face {
  font-family: "Fira Code";
  src: url("/fonts/FiraCode-Regular.eot");
  src: url("/fonts/FiraCode-Regular.eot?#iefix")
      format("embedded-opentype"),
    url("/fonts/FiraCode-Regular.svg#FiraCode-Regular") format("svg"),
    url("/fonts/FiraCode-Regular.ttf") format("truetype"),
    url("/fonts/FiraCode-Regular.woff") format("woff"),
    url("/fonts/FiraCode-Regular.woff2") format("woff2");
  font-weight: normal;
  font-style: normal;
}

* {
  box-sizing: border-box;
}

body {
  display: flex;
  place-items: center;
  margin: 0;
  height: 100vh;
  width: 100vw;
}

#app {
  font-family: "Fira Code", monospace;
  background-color: white;
}
</style>
