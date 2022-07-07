<template>
  <button class="active:shadow-lg shadow-inner border border-grey" :class="props.class">
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
const props = defineProps({
  class: {
    type: String,
    default: "",
  },
});
</script>

<style scoped>
button {
  font-size: 3rem;
}
</style>