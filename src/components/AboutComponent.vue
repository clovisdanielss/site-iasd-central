<template>
  <div id="about-component" class="row">
    <div class="col">
      <div class="mt-3">
        <h1>Sobre a Igreja Adventista do Sétimo Dia (IASD)</h1>
        <hr />
      </div>
      <div class="blog-post">
        <p>
          Os adventistas do sétimo dia, com mais de 17 milhões de membros no mundo,
          são membros de uma igreja cristã protestante organizada em 1863 nos Estados Unidos.
          Sua origem ocorre logo depois do movimento liderado por Guilherme Miller, que ressaltou
          a necessidade de maior ênfase na pregação sobre a breve volta de Jesus Cristo a esse mundo.
          A sede sul-americana da Igreja Adventista do Sétimo Dia, responsável pela coordenação
          administrativa em oito países, registra mais de dois milhões de membros.
        </p>
        <p>
          Para saber mais sobre a igreja de forma geral,
          <a
            target="_blank"
            href="https://www.adventistas.org/pt/institucional/os-adventistas/quem-sao-os-adventistas/"
          >clique aqui!</a>
        </p>
        <hr />
      </div>

      <div class="mt-3">
        <h1>Sobre a IASD Central de Fortaleza</h1>
        <hr />
      </div>
      <div class="blog-post">
        <p >{{text}}</p>
        <p> Se quiser ver sua rota até nossa igreja <a target="_blank" href="https://www.google.com/maps/place/3%C2%B043'44.9%22S+38%C2%B032'04.2%22W/@-3.7291389,-38.535597,18z/data=!3m1!4b1!4m13!1m6!3m5!1s0x0:0x16b92984a03550e5!2sIgreja+Adventista+do+S%C3%A9timo+Dia+Central+de+Fortaleza!8m2!3d-3.7292452!4d-38.534502!3m5!1s0x0:0x0!7e2!8m2!3d-3.7291487!4d-38.5344964"> clique aqui!</a></p>
        <hr />
      </div>

      <GmapMap
        :center="{lat:-3.729149, lng:-38.534496}"
        :zoom="18"
        map-type-id="terrain"
        style="width: 100%; height: 300px"
      >
        <GmapMarker :position="google && new google.maps.LatLng(-3.729149,-38.534496)" />
      </GmapMap>
    </div>
  </div>
</template>

<script>
import { gmapApi } from "vue2-google-maps";
export default {
  name: "AboutComponent",
  data() {
    return {
      text: `
        A IASD central de Fortaleza, foi a primeira igreja adventista
         a ser construída em Fortaleza. Ela se localiza no Centro de Fortaleza, como você pode observar
         no mapa. Te aguardamos lá!
      `
    };
  },
  computed: {
    google: gmapApi
  }
};
</script>