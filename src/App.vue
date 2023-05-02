<template>
  <NavbarComponent :logo="logoSrc" :alt="appName" />
  <router-view />
  <FooterComponent />
</template>

<style>
* {
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>

<script>
import NavbarComponent from "./components/NavbarComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";

export default {
  components: {
    NavbarComponent,
    FooterComponent
  },
  data() {
    return {
      logoSrc: "/assets/images/logo.png",
      appName: "Make Your Burger",
    }
  }
}
</script>