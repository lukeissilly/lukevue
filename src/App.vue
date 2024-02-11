<template>
  <nav>

    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/socials">Socials</router-link>
    
  </nav>
  <router-view/>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
}

nav {
  padding: 30px;
  padding-bottom: 100px;

  a {
    font-weight: bold;
    color: #ffffff;
    font-weight: lighter;

    &.router-link-exact-active {
      color: #ffffff;
      font-weight: 900;
    }
  }
}
</style>
