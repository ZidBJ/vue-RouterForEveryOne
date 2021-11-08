<template>
  <nav id="nav">
    <p class="logo">The Vue School Travel App</p>
    <ul class="nav-links">
      <li class="links"><router-link to="/">Home</router-link></li>
      <li
        v-for="destination in destinations"
        :key="destination.name"
        class="links"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug },
          }"
          >{{ destination.name }}</router-link
        >
      </li>
      <li>
        <router-link :to="{ name: 'User' }">Dashboard</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import store from "@/store";
export default {
  data() {
    return {
      destinations: store.destinations,
    };
  },
};
</script>

<style  scoped>
.nav-links {
  display: flex;
}

.links {
  padding-right: 20px;
  list-style: none;
}
.links:hover {
  text-decoration: underline;
}

#nav a.router-link-exact-active {
  color: #ab26ab;
}
.logo {
  font-size: 20px;
  color: purple;
  font-weight: bold;
}
</style>