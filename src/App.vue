<script setup>
import { useStoreCounter } from './stores/counter';
import HelloPinia from './components/HelloPinia.vue';
const counter = useStoreCounter();
</script>

<template>
  <h1>Pinia入門</h1>
  <p>Count: {{ counter.count }}</p>
  <HelloPinia />
</template>
