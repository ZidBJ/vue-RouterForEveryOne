<template>
  <div>
    <router-link :to="{ name: 'Invoices' }">Invoices</router-link>
    <h1>User Page</h1>
    <h1>User Name is: {{ sUserName }}</h1>
    <button @click="logout">logout</button>
  </div>
</template>

<script>
import store from "../store.js";

export default {
  data() {
    return { sUserName: store.user };
  },
  methods: {
    logout() {
      store.user = null;
      this.$router.push({ name: "Home" });
    },
  },
};
</script>

<style scoped>
</style>