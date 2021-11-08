<template>
  <div>
    <h1>Not Found</h1>
    <p>
      Oops We couldn't find That Page. Try Going
      <router-link :to="{ name: 'Home' }">Home</router-link>
    </p>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
</style>