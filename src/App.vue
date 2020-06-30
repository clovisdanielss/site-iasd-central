<template>
  <div id="app">
    <nav id="nav" class="navbar navbar-expand-lg navbar-dark bg-dark pt-0 pb-0">
      <router-link to="/" class="navbar-brand  pt-0 pb-0" >
      <img src="logo.png" class="logo"/></router-link>
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
            <router-link to="/" class="nav-link p-3">
              Início
              <span class="sr-only">(current)</span>
            </router-link>
          </li>
          <li class="nav-item" @click="setActive">
            <router-link to="/about" class="nav-link  p-3">Sobre</router-link>
          </li>
          <li class="nav-item " @click="setActive">
            <router-link to="/contact" class="nav-link p-3">Contato</router-link>
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

<style scoped>
.nav-item{
  transition: background-color 1s;
}

.nav-item:hover{
  background-color:gray;
}

.logo{
  max-height: 50px;
  padding: 4px 0px;
}

@media(max-width: 991px){
  .logo{
    margin: 5px 0px;
  }
}
</style>

