<template>
  <div id="app">
    <nav class="navbar navbar-expand navbar-dark bg-warning">
      <div class= "nav bavbar-bar">
      <router-link to="/" class="nav-item nav-link active">Home</router-link> |
      <router-link to="/about"  class="nav-item nav-link">About</router-link>|
      <router-link to="/categories"  class="nav-item nav-link">Categories</router-link>|
 
    
    </div>
    </nav>
    <router-view/>
    <a href="http://localhost/app/categories/">Categories</a>
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
