<template>
  <nav>
    <router-link to="/">Benvinguda</router-link>
    <router-link to="/home">Pressupost</router-link>
  </nav>
  <RouterView />
</template>

<script setup>

</script>

<style scoped>
nav {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  padding: 30px;
  text-align: center;
}

nav a {
  text-decoration: none;
  color: gray;
  margin: 0 10px;
}

nav a.router-link-exact-active {
  font-weight: bold;
  color: black;
}
</style>
