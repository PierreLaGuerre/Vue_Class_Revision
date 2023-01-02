<template>
  <header class="bg-blue-500 text-white py-4">
    <div class="container mx-auto flex items-center justify-between">
      <h1 class="font-bold text-2xl">My App</h1>
      <nav>
        <ul class="flex">
          <li class="mr-6">
            <router-link to="/home" class="text-white hover:text-blue-300">Home</router-link>
          </li>
          <li class="mr-6">
            <router-link to="/" class="text-white hover:text-blue-300">Auth</router-link>
          </li>
          <li class="mr-6">
            <router-link to="/favorites" class="text-white hover:text-blue-300">Favorites</router-link>
          </li>
          <li class="mr-6">
            <a
              class="text-white hover:text-blue-300"
              :href="link"
              target="_blank"
              >{{ search }}</a
            >
          </li>
          <li class="mr-6">
            <button
              class="p-2 bg-orange-500 rounded-sm"
              :href="link"
              target="_blank"
              @click="changeSearch"
            >
              Change Search
            </button>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue';

const link = ref("https://chat.openai.com/chat")
const search = ref("Ask GPT");

function changeSearch() {
  if (search.value === "Ask GPT") {
    search.value = "Ask Google";
  link.value = "https://google.com";
  } else {
  search.value = "Ask GPT";
  link.value = "https://chat.openai.com/chat";
}
}
</script>

<style scoped></style>
