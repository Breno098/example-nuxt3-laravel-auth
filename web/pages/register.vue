<script lang="ts" setup>
  import { useAuthStore } from '~/stores/useAuthStore';

  const form = ref({
    name: "",
    email: "",
    password: "",
    password_confirmation: ""
  });

  const auth = useAuthStore();

  async function handleRegister() {
    const { error } = await auth.register(form.value)

    if (! error.value) {
      navigateTo("/");
    }
  }
</script>

<template>
  <div>
    <form @submit.prevent="handleRegister">
      <label>
        Name 
        <input type="text" v-model="form.name">
      </label>

      <br/>

      <label>
        Email 
        <input type="email" v-model="form.email">
      </label>

      <br/>

      <label>
        Password 
        <input type="password" v-model="form.password">
      </label>

      <br/>

      <label>
        Password Confirmation
        <input type="password" v-model="form.password_confirmation">
      </label>

      <button>
        Register
      </button>
    </form>
  </div>
</template>

<style scoped></style>
