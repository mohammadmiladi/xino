<template>
  <div>
    <Home />
    <Footer />
  </div>
</template>

<script>
import Home from "./components/Home.vue";
import Footer from "./components/common/Footer.vue";

export default {
  name: "App",
  components: {
    Home,
    Footer,
  },
};
</script>

<style>
body {
  margin: 0 !important;
}
</style>
