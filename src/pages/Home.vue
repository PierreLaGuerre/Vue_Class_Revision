<template>
 <div>
     <h2 class=" text-2xl text-center mt-5">Welcome, {{ user.username }}</h2>
     </div>
     <div class=" grid grid-cols-3 gap-4">
        <Card v-for="product in products" :product="product"/>
     </div>
</template>

<script setup>
import {ref} from 'vue';
import Card from '../components/Card.vue';
import { useUserStore } from '../stores/user';

const user = useUserStore();

const products = ref([]);
async function getProducts() {
    const res = await fetch('https://makeup-api.herokuapp.com/api/v1/products.json?brand=covergirl&product_type=lipstick')
    const finalRes = await res.json();
    products.value = finalRes;
}
getProducts();
</script>

<style scoped>

</style>