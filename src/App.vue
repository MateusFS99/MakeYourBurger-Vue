<template>
  <NavbarComponent />
  <router-view />
  <FooterComponent />
</template>

<style></style>

<script>
import NavbarComponent from "./components/NavbarComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";

export default {
  components: {
    NavbarComponent,
    FooterComponent
  }
}
</script>