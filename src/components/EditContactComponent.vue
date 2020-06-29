<template>
  <form class="my-modal col-md-12 card border m-auto p-3">
    <div class="row">
      <div class="col">
        <h1>Modificar Departamentos</h1>
        <div class="icon" @click.prevent="onClose">
          <i class="fas fa-times" @click.prevent="onClose"></i>
        </div>
        <hr />
      </div>
    </div>
    <div class="row">
      <div class="col-xl-12 relative mh-500">
        <div class="btn-group btn-100">
          <button
            type="button"
            class="btn btn-block btn-secondary dropdown-toggle"
            data-toggle="dropdown"
            data-display="static"
            aria-haspopup="true"
            aria-expanded="false"
            @click.prevent="onClean"
          >{{selected >= 0 ? departamentsToUpdate[selected].name : "Adicionar Departamento"}}</button>
          <div class="dropdown-menu dropdown-menu-lg-right">
            <button
              class="dropdown-item"
              type="button"
              v-for="(departament,index) in departamentsToUpdate"
              :key="index"
              @click="onSelect(index)"
            >{{departament.name}}</button>
            <button
              class="dropdown-item"
              type="button"
              :key="-1"
              @click="onAddDepartament"
            >Adicionar Departamento</button>
          </div>
        </div>
        <div v-if="selected == -1" class="row">
          <div class="col-xl-12 p-3">
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">Nome</span>
              </div>
              <input
                type="text"
                class="form-control"
                placeholder="Nome"
                aria-label="title"
                aria-describedby="basic-addon1"
                v-model="departamentsToUpdate[departamentsToUpdate.length-1].name"
              />
            </div>
          </div>
          <div class="col-xl-12 m-0">
            <button
              v-on:click.prevent="onDefineDepartamentName"
              type="submit"
              class="btn btn-secondary btn-block mt-3"
            >Adicionar</button>
          </div>
        </div>
        <div v-else>
          <div class="row m-0 btn-100 m-0">
            <button
              v-on:click.prevent="onRemoveDepartament"
              type="button"
              class="btn btn-secondary btn-block mt-3"
            >Remover Departamento</button>
          </div>

          <div class="absolute row">
            <div
              class="row p-3 m-0"
              v-for="(member,index) in departamentsToUpdate[selected].members"
              :key="index"
            >
              <span class="float" @click="onRemoveMember(index)">
                <i class="fas fa-times"></i>
              </span>
              <div class="p-0">
                <div class="input-group mb-3">
                  <div class="input-group-prepend">
                    <span class="input-group-text" id="basic-addon1">Nome</span>
                  </div>
                  <input
                    type="text"
                    class="form-control"
                    placeholder="Nome"
                    aria-label="title"
                    aria-describedby="basic-addon1"
                    v-model="member.name"
                  />
                </div>
              </div>
              <div class="p-0">
                <div class="input-group mb-3">
                  <div class="input-group-prepend">
                    <span class="input-group-text" id="basic-addon1">Contato</span>
                  </div>
                  <input
                    type="text"
                    class="form-control"
                    placeholder="985441322"
                    aria-label="image"
                    aria-describedby="basic-addon1"
                    v-model="member.contact"
                  />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-if="selected >= 0" class="row m-0 btn-100 m-0 btn-pos">
          <button
            v-on:click.prevent="onAddMember"
            type="button"
            class="btn btn-secondary btn-block mt-3"
          >Adicionar Membro</button>
        </div>
    <div class="row m-0">
      <button
        v-on:click.prevent="onSubmit"
        type="submit"
        class="btn btn-secondary btn-lg btn-block mt-3"
      >Atualizar</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "EditContactComponent",
  data() {
    return {
      selected: 0,
      departamentsToUpdate: this.departamentsArray
    };
  },
  methods: {
    onClean() {
      let departaments = [];
      if (this.departamentsToUpdate.length === 1) {
        return;
      }
      this.departamentsToUpdate.map(item => {
        if (item.name.trim() !== "") {
          departaments.push(item);
        }
      });
      this.departamentsToUpdate = departaments;
    },
    onSelect(index) {
      this.selected = index;
    },
    onSubmit() {
      this.submit(this.departamentsToUpdate);
    },
    onAddMember() {
      this.departamentsToUpdate[this.selected].members.push({
        name: "",
        contact: ""
      });
    },
    onRemoveMember(index) {
      console.log(index);
      this.departamentsToUpdate[this.selected].members.splice(index, 1);
    },
    onAddDepartament() {
      this.selected = -1;
      this.departamentsToUpdate.push({
        name: "",
        members: [{ name: "", contact: "" }]
      });
    },
    onDefineDepartamentName() {
      let len = this.departamentsToUpdate.length - 1;
      this.selected = len;
    },
    onRemoveDepartament() {
      this.departamentsToUpdate.splice(this.selected, 1);
      if (this.departamentsToUpdate.length === 0) {
        this.selected = -1;
        this.onAddDepartament();
        return;
      }
      this.selected = 0;
    }
  },
  props: {
    departamentsArray: {
      type: Array
    },
    submit: {
      type: Function
    },
    onClose: {
      type: Function
    }
  }
};
</script>

<style scoped>
.float {
  float: right;
}

.mh-500 {
  min-height: 400px;
}
.btn-100 {
  width: 100% !important;
}
.my-modal {
  z-index: 1;
  position: absolute;
  bottom: 10px;
  right: 10px;
  width: 50%;
}
.icon {
  position: absolute;
  right: 20px;
  top: 10px;
}
.float > i,
.icon > i {
  transition: color 0.5s;
}
.float > i:hover,
.icon > i:hover {
  color: #d0d0d0;
}

.relative {
  position: relative;
  overflow-y: scroll;
}

.absolute {
  position: absolute;

  width: 100%;
}

.absolute > .row {
  width: 100%;
  justify-content: space-between;
}

.absolute > .row > div {
  width: 47%;
}

@media (max-width: 1024px) {
  .absolute > .row > div {
    width: 100%;
  }
}

@media (max-width: 720px) {
  .my-modal {
    z-index: 0;
    position: initial;
    width: 100%;
  }
  .mh-500 {
    min-height: 400px;
  }
  .absolute > .row > div {
    width: 100%;
  }
}

@media (max-height: 720px) {
  .mh-500 {
    min-height: 300px;
  }
}

.absolute-b-0 {
  position: absolute;
  left: 0px;
  bottom: 0px;
}
</style>