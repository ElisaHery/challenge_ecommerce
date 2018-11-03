<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Accueil</router-link> |
      <router-link to="/produits">Produits</router-link>
    </div>
    <div id="occupe_espace"></div>
    <router-view/>
  </div>
</template>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  height: 50px;
  line-height: 50px;
  margin: 0;
  background: #0b1624;
  position: fixed;
  width: 100%;
  a {
    text-decoration: none;
    font-weight: bold;
    color: white;
    &.router-link-exact-active {
      text-decoration: underline;
    }
  }
}

#occupe_espace {
  height: 50px;
}
</style>
