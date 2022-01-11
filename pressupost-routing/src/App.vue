<template>
  <div id="nav">
    <router-link to="/">Calculadora</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/Contacta">Contacta</router-link>
  </div>
  <router-view/>
</template>

<style>
/* Els estils de la class="Home"  */
#app {      
  font-family: Avenir, Helvetica, Arial, sans-serif;    
  color: #2c3e50;  
}

#app > div {
  width: 40%;
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
