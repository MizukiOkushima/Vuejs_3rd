<script setup>
import { useStoreCounter } from './stores/counter';
import HelloPinia from './components/HelloPinia.vue';
import { storeToRefs } from 'pinia';
const counter = useStoreCounter();
const { count, doubleCount } = storeToRefs(counter);
const { increment } = counter;

// counter.$subscribe((mutation, state) => {
//   console.log('mutation:', mutation);
//   console.log('state:', JSON.stringify(state));
// });

const unsubscribe = counter.$onAction(
  (
    {
      name,
      store,
      args,
      after,
      onError,
    }
  ) => {
    const startTime = Date.now();
    console.log(`Start "${name}" with params [${args.join(',')}].`);

    after((result) => {
      console.log(
        `Finished "${name}" after ${Date.now() - startTime}ms.\nResult: ${result}`
      );
    });

    onError((error) => {
      console.warn(
        `Failed "${name}" after ${Date.now() - startTime}ms.\nError:${error}.`
      );
    });
  }
);

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
