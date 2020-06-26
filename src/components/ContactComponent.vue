<template>
  <div id="contact-component" class="col">
    <div class="mt-3 col p-0">
      <h1>Contato</h1>
      <hr />
    </div>
    <div class="row">
      <div class="col-md-7">
        <div class="blog-post p-1">
          <p class="text-justify">
            Bem, para contatar qualquer um de nossos líderes, basta clicar no
            departamento indicado na tabela a seguir. Com isso, você pode ver o
            número do líder e contata-lo. É importante saber, que qualquer um
            desses pode também indicar um estudo bíblico para você.
          </p>
        </div>
      </div>
      <div class="col-md-5 card">
        <table class="table">
          <thead>
            <tr>
              <th scope="col">Departamentos</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(departament,index) in departamentsArray" :key="index">
              <td v-bind:data-index="index" @click.prevent="onShowElement">
                {{departament.name}}
                <p v-bind:id="'departamento-icon-' + index" class="icon-info">+</p>
                <div v-bind:id="'departamento-' + index" class="td-info hide">
                  <hr />
                  <div v-for="(member,index) in departament.members" :key="index" class="row">
                    <div class="col">
                      <h6>Nome:</h6>
                      <h6>Contato:</h6>
                    </div>
                    <div class="col">
                      <h6>{{member.name}}</h6>
                      <h6>{{member.contact}}</h6>
                    </div>
                    <hr />
                  </div>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ContactComponent",
  data() {
    return {
      departamentsArray: [
        {
          name: "Pastoral",
          members: [{ name: "Pr. Erivonaldo Batista", contact: "99798-6850" }]
        },
        {
          name: "Administração",
          members: [{ name: "Océlio", contact: "8609-9207" }]
        },
        {
          name: "Tesouraria",
          members: [{ name: "Júnior Torres", contact: "3496-3235" }]
        }
      ]
    };
  },
  methods: {
    onShowElement(event) {
      let index = event.target.getAttribute("data-index");
      if (!index) {
        return;
      }
      let id = "departamento-" + index;
      let idIcon = "departamento-icon-" + index;
      let ele = document.getElementById(id);
      let icon = document.getElementById(idIcon);
      if (ele.classList.contains("hide")) {
        ele.classList.remove("hide");
        icon.innerText = "-";
      } else {
        ele.classList.add("hide");
        icon.innerText = "+";
      }
    }
  }
};
</script>

<style scoped>
.icon-info {
  float: right;
}
.td-info {
  overflow: hidden;
  height: 100px;
}

.td-info.hide {
  height: 0px;
  pointer-events: none;
}
</style>