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
  src: url("@/../public/fonts/FiraCode-Regular.eot");
  src: url("@/../public/fonts/FiraCode-Regular.eot?#iefix")
      format("embedded-opentype"),
    url("@/../public/fonts/FiraCode-Regular.svg#FiraCode-Regular") format("svg"),
    url("@/../public/fonts/FiraCode-Regular.ttf") format("truetype"),
    url("@/../public/fonts/FiraCode-Regular.woff") format("woff"),
    url("@/../public/fonts/FiraCode-Regular.woff2") format("woff2");
  font-weight: normal;
  font-style: normal;
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
  width: 100%;
  height: 100%;
  display: flex;
  place-items: center;
  background-color: black;

}
</style>
