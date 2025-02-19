<script setup>
import { useStoreCounter } from '../stores/counter';
const counter = useStoreCounter();

// const patch = () => {
//   counter.$patch({
//     count: 100,
//     user: {
//       name: 'Jane Doe',
//     },
//   });
// };

const patch = () => {
  counter.$patch((state) => {
    state.count = 10;
    state.user.name = 'Kevin Doe';
  });
};

const replace = () => {
  counter.$state = {
    count: 100,
    count2: 200,
    user: {
      name: 'Jane Doe',
    },
  };
};
</script>

<template>
  <h2>Hello Pinia</h2>
  <p>カウント:{{ counter.count }}</p>
  <button @click="counter.$reset">Reset</button>
  <button @click="patch">Patch</button>
  <button @click="replace">Replace</button>
</template>