<template>
  <footer id="footer-component" class="footer">
    <div>
      <span class="text-muted">@Copyright © 2020</span>
      <span class="text-muted">Av. do Imperador, 891, Fortaleza - Ceará</span>
      <span class="text-muted">IASD Central de Fortaleza</span>
      <div class="flexbox">
        <a href="https://www.instagram.com/adventistascentralfort_/" target="_blank">
            <span>
            <i class="fab fa-instagram font-24"></i>
            </span>
        </a>
        <a href="https://www.youtube.com/channel/UCtLLF9rxTDs1ADpShyef7Sw" target="_blank">
            <span>
            <i class="fab fa-youtube font-24"></i>
            </span>
        </a>
      </div>
      <span class="text-muted">contato@iasdcentralfortaleza.org.br</span>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterComponent"
};
</script>

<style scoped>
.footer {
  left: 0;
  position: absolute;
  bottom: 0;
  width: 100%;
  height: auto;
  background-color: #f5f5f5;
  font-size: 12px !important;
}

.font-24 {
  font-size: 30px !important;
}

a {
  text-decoration: none !important;
  color: black;
}

.footer > div {
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
span {
  padding: 2px;
}

@media(max-width: 578px){
    .footer{
        position: unset;
    }
    .flexbox{
        display: flex;
        justify-content: space-around;
        flex-direction: row;
    }
}
</style>