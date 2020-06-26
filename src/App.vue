<template>
  <div id="app">
    <nav id="nav" class="navbar navbar-expand-lg navbar-dark bg-dark">
      <router-link to="/" class="navbar-brand">IASDCF</router-link>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active" @click="setActive" id="home-link">
            <router-link to="/" class="nav-link">
              Início
              <span class="sr-only">(current)</span>
            </router-link>
          </li>
          <li class="nav-item" @click="setActive">
            <router-link to="/about" class="nav-link">Sobre</router-link>
          </li>
          <li class="nav-item" @click="setActive">
            <router-link to="/contact" class="nav-link">Contato</router-link>
          </li>
        </ul>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      activeLink:null
    };
  },
  mounted(){
    this.activeLink = document.getElementById("home-link")
  },
  methods: {
    setActive(event) {
      event.target.classList.add("active");
      if(this.activeLink){
        this.activeLink.classList.remove("active");
      }
      this.activeLink = event.target;
    }
  }
};
</script>

<style>
</style>
