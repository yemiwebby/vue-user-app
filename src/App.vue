<template>
  <div>
    <NavBar />

    <UserList message="List of Users" />

    <div class="container"></div>
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import UserList from "./components/UserList.vue";

export default {
  name: "App",
  components: { NavBar, UserList },
};
</script>

<style>
body {
  background: #eee;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.page-title {
  margin: 15px 15px;
}
</style>
