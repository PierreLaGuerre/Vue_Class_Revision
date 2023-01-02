<template>
   
  <div class="bg-white py-8 px-4 shadow-md rounded-lg">
    <form @submit.prevent="login" class="mx-auto max-w-lg">
      <h1 class="text-2xl font-bold mb-4">Log In</h1>
      <div class="mb-4">
        <label for="email" class="block text-gray-700 text-sm font-bold mb-2">Email</label>
        <input v-model="email" id="email" type="text" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" />
      </div>
      <p class=" text-red-600 text-xs" v-if="showError">Necesitas una arroba</p>
      <div class="mb-6">
        <label for="password" class="block text-gray-700 text-sm font-bold mb-2">Password</label>
        <input v-model="password" id="password" type="password" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" />
      </div>
      <div class="flex items-center justify-between">
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit">
          Log In
        </button>
        <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" href="#">
          Forgot Password?
        </a>
      </div>
    </form>
  </div>

</template>

<script setup>
import { ref, watch } from 'vue';
import { useRouter } from 'vue-router'
import { useUserStore } from '../stores/user';
const router = useRouter();
const user = useUserStore();
const showError = ref(false);

const email = ref('');
const password = ref('');

watch(email, (newEmail, oldEmail) => {
  if(!newEmail.includes('@')) {
    showError.value = true;
  } else {
    showError.value = false;
  }
})

function login() {
user.username = email.value;
router.push("/home");
}
</script>

<style scoped>

</style>