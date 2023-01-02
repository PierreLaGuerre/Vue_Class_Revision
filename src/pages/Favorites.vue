<template>
    <h2 class=" text-lg">Total de favoritos: {{ productCount }}</h2>  
    <div class="grid grid-cols-1 ">
        <Card v-for="product in piniaProduct.products" :product="product" />
    </div>
  
</template>

<script setup>
import { useProductsStore } from '../stores/products';
import Card from '../components/Card.vue';
import { computed } from 'vue';

const piniaProduct = useProductsStore();
const productCount = computed(() => piniaProduct.products.length);

</script>

<style scoped>

</style>