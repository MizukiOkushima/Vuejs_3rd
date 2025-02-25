<script setup>
import { onMounted } from 'vue';
import { storeToRefs } from 'pinia';
import { useStoreProducts } from '../stores/products';
import { useStoreCart } from '../stores/cart';

const { products } = storeToRefs(useStoreProducts());
const { getProducts } = useStoreProducts();
const { addCart } = useStoreCart();

onMounted(() => {
    getProducts();
});
</script>
<template>
    <ul>
        <li v-for="product in products" v-bind:key="products.id">
            {{ product.title }} - &yen;{{ product.price.toLocaleString() }}
            <button @click="addCart(product)" :disabled="!product.inventory">カートへ</button>
        </li>
    </ul>
</template>
<!-- <script setup>
import { onMounted, ref } from 'vue';
import shop from '../api/shop.js';
const products = ref([]);
onMounted(() => {
    shop.getProducts((data) => (products.value = data));
});
</script>
<template>
    <ul>
        <li v-for="product in products" v-bind:key="product.id">
            {{ product.title }} - &yen;{{ product.price.toLocaleString() }}
        </li>
    </ul>
</template> -->