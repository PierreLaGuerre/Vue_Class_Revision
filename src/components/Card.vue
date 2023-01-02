<template>
  <div class="bg-white rounded-lg shadow-lg p-6">
    <div class="flex items-center justify-between">
      <img :src="product.image_link" alt="Product image" class="w-32 h-32 rounded-full" />
      <div class="ml-6">
        <h2 class="text-2xl font-bold text-gray-800">{{ product.name }}</h2>
        <p class="text-gray-600 text-sm">{{ product.description }}</p>
        <div class="mt-4 flex items-center">
          <p class="text-lg font-bold text-gray-800">${{ product.price }}</p>
          <button @click="addToCart" class="ml-4 px-4 py-2 rounded-full bg-blue-500 text-white font-bold hover:bg-blue-700 focus:outline-none focus:shadow-outline"
          >
            Add to Cart
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
 
<script setup>
import { useProductsStore } from '../stores/products';
const piniaProduct = useProductsStore();
const props = defineProps(["product"]);


function addToCart() {
  piniaProduct.piniaAddToCart(props.product);
}
</script>

<style scoped></style>