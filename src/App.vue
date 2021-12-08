<template>
  <div id="nav">
    <router-link :class="{active: $route.name === 'Home'}" to="/">Home</router-link> 
    <router-link :class="{active: $route.name === 'Cart'}" to="/cart">Cart</router-link>
  </div>
  <router-view />
</template>

<script>
  export default {
    mounted() {
      this.$store.commit("updateCartFromLocalStorage")
    }
  }
</script>


<style>
#app {
  font-family: "Roboto";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
}

html, body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

body {
  background-color: rgb(142, 202, 230);
}

#nav {
  padding: 1rem;
  width: 100%;
  height: 3rem;
  background-color: rgb(33, 158, 188);
  line-height: 2rem;
}

 a {
    font-weight: 900;
    color: black;
    text-decoration: none;
    font-size: 2.1rem;
    margin: 0 3rem 0 3rem;
  }

  a:hover {
    background-color: rgb(159, 201, 255);
    padding: 1.8rem;
  }
</style>
