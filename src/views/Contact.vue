<template>
  <div id="contact-view" class="container-xl">
    <ContactComponent></ContactComponent>
    <FooterComponent></FooterComponent>
  </div>
</template>

<script>
import ContactComponent from "../components/ContactComponent.vue";
import FooterComponent from "../components/FooterComponent.vue";

export default {
  name: "Contact",
  components: {
    ContactComponent,
    FooterComponent
  }
};
</script>