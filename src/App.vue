<template>
  <div id="app">
    <div class="container">
      <pp-header></pp-header>
    </div>
    <div class="container">
      <pp-admin></pp-admin>
    </div>
    <div class="container">
      <pp-footer></pp-footer>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Footer from "@/components/Footer";
// import Home from "@/components/Home";
import Admin from "@/components/Admin";

export default {
  components: {
    ppHeader: Header,
    ppFooter: Footer,
    // ppHome: Home,
    ppAdmin: Admin
  }
};
</script>

<style></style>
