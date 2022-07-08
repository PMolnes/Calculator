<template>
  <button :disabled="props.disabled" class="active:shadow-lg shadow-inner border border-grey" :class="props.class">
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
const props = defineProps({
  class: {
    type: String,
    default: "",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
});
</script>

<style scoped>
button {
  font-size: 3rem;
}
</style>