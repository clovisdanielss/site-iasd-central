<template>
  <div>
    <div id="about-view" class="container-xl">
      <AboutComponent></AboutComponent>
    </div>
    <FooterComponent></FooterComponent>
  </div>
</template>

<script>
import AboutComponent from "../components/AboutComponent.vue";
import FooterComponent from "../components/FooterComponent.vue";

export default {
  name: "About",
  components: {
    AboutComponent,
    FooterComponent
  }
};
</script>