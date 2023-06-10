<script setup>
  import { ref, reactive, onMounted } from 'vue'

  // const email = ref('')
  // const password = ref('')

  const user = reactive({
    email: '',
    password: ''
  })

  const names = reactive([])

  onMounted(() => {
    names.push(
      {
        firstName: 'John',
        age: '20'
      },
      {
        firstName: 'Jane',
        age: '30'
      }
    )
  })

  function login() {
    console.log(user.email, user.password);
  }

  function remove(user) {
    const index = names.findIndex((name) => name.firstName === user.firstName)
    names.splice(index, 1)
  }

</script>

<template>
  <h1 class="text-blue-900 font-bold text-3xl">Login</h1>

  <template v-if="names.length > 0">
    <ul>
      <li v-for="name in names">{{ name.firstName }} - <button v-on:click="remove(name)">remove</button></li>
    </ul>
  </template>
  <template v-else>Nenhum user encontrado</template>

  <form action="" @submit.prevent="login">
    <input type="text" placeholder="Email" v-model="user.email">
    <input type="text" placeholder="Senha" v-model="user.password">

    <button type="submit">Login</button>
  </form>
</template>

<style></style>

