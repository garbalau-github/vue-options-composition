<template>
  <nav>
    <router-link to="/">Options API</router-link> |
    <router-link to="/composition">Composition API</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

input {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px 10px;
}

ul {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  width: 250px;
  margin: 20px auto 0;
}

li {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  margin: 7.5px;
  display: flex;
  justify-content: space-between;
}
</style>
