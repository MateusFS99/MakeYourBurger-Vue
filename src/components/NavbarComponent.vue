<template>
  <div id="navbar">
    <router-link to="/" id="logo-url">
      <img :src="logo" :alt="alt" id="logo">
    </router-link>
    <router-link to="/">Home</router-link>
    <router-link to="/pedidos">Pedidos</router-link>
  </div>
</template>

<style scoped>
#navbar {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#navbar #logo-url {
  margin: auto;
  margin-left: 0;
}

#logo {
  width: 40px;
  height: 40px;
}

#navbar a {
  color: #FCBA03;
  text-decoration: none;
  margin: 12px;
  transition: .5s;
}

#navbar a:hover {
  color: #FFF
}
</style>

<script>
export default {
  props: {
    logo: String,
    alt: String
  }
}
</script>