<script setup>
import { useStoreCounter } from './stores/counter';
import HelloPinia from './components/HelloPinia.vue';
import { storeToRefs } from 'pinia';
const counter = useStoreCounter();
const { count, doubleCount } = storeToRefs(counter);
const { increment } = counter;
</script>

<template>
  <h1>Pinia入門</h1>
  <p>Count: {{ count }}</p>
  <p>DoubleCount: {{ doubleCount }}</p>
  <div>
    <button @click="increment">up</button>
  </div>
  <HelloPinia />
</template>
