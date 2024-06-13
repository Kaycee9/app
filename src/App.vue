<template>
  <div>
    <h1>AMTES ATTENDANCE SYSTEM</h1>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/register">Register</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#myBody {
  background: linear-gradient(
    to right,
    white,
    rgb(97, 135, 148),
    rgb(73, 127, 148)
  );
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
</style>
