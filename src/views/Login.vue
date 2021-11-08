<template>
  <div>
    <h1>Login</h1>
    <div class="form">
      <label for="userName">User Name</label>
      <input v-model="userName" type="text" name="userName" class="input" />
      <label for="password">Password</label>
      <input v-model="password" type="password" name="password" class="input" />
      <button @click="login" class="btn">Login</button>
    </div>
    <h1>User Name is: {{ sUserName }}</h1>
  </div>
</template>

<script>
import store from "../store.js";
export default {
  data() {
    return {
      userName: null,
      password: null,
      sUserName: store.user,
    };
  },
  methods: {
    login() {
      store.user = this.userName;
      const redirectPath = this.$route.query.redirect || { name: "Home" };
      this.$router.push(redirectPath);
    },
  },
};
</script>

<style scoped>
</style>