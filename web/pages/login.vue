<script lang="ts" setup>
  definePageMeta({
    middleware: ['guest']
  })

  import { useAuthStore } from '~/stores/useAuthStore';

  const form = ref({
    email: 'test@example.com',
    password: 'password'
  });

  const auth = useAuthStore();

  async function handleLogin() {
    const { error } = await auth.login(form.value)

    if(! error.value) {
      return navigateTo("/");
    }
  }
</script>

<template>
  <div>
    <form @submit.prevent="handleLogin">
      <label>
        Email 
        <input type="email" v-model="form.email">
      </label>

      <br/>

      <label>
        Password 
        <input type="password" v-model="form.password">
      </label>

      <button>
        Login
      </button>
    </form>
  </div>
</template>

<style scoped></style>
