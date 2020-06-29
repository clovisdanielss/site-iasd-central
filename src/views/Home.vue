<template>
  <div class="">
    <div id="home-view" class="container-fluid">
      <HomeComponent></HomeComponent>
    </div>
    <FooterComponent></FooterComponent>
  </div>
</template>

<script>
import HomeComponent from "../components/HomeComponent.vue";
import FooterComponent from "../components/FooterComponent.vue";

export default {
  name: "Home",
  components: {
    HomeComponent,
    FooterComponent
  }
};
</script>
