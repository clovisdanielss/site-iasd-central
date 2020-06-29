<template>
  <form class="my-modal col-md-12 card border m-auto p-3">
    <div class="row">
      <div class="col">
        <h1>Modificar "Sobre IASD Central"</h1>
        <div class="icon" @click.prevent="onClose">
          <i class="fas fa-times" @click.prevent="onClose"></i>
        </div>
        <hr />
      </div>
    </div>
    <div class="row">
      <div class="col-xl">
        <div class="input-group">
          <div class="input-group-prepend">
            <span class="input-group-text">Texto de Informações</span>
          </div>
          <textarea v-model="textToUpdate" class="form-control mh-500" aria-label="With textarea"></textarea>
        </div>
      </div>
    </div>
    <button
      v-on:click.prevent="onSubmit"
      type="submit"
      class="btn btn-secondary btn-lg btn-block mt-3"
    >Atualizar</button>
  </form>
</template>

<script>
export default {
  name: "EditAboutComponent",
  data(){
    return{
      textToUpdate:this.text
    }
  },
  methods: {
    onSubmit() {
      this.submit(this.textToUpdate);
    }
  },
  props: {
    text: {
      type: String
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
.mh-500 {
  min-height: 400px;
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
.icon > i {
  transition: color 0.5s;
}
.icon > i:hover {
  color: #d0d0d0;
}
@media (max-height: 800px) {
  .mh-500 {
    min-height: auto;
  }
}

@media (max-width: 720px) {
  .my-modal {
    z-index: 0;
    position: initial;
    width: 100%;
  }
  .mh-500{
    min-height: 400px;
  }
}

@media (max-height: 720px) {
  .my-modal {
    z-index: 0;
    position: initial;
    width: 100%;
  }
  .mh-500 {
    min-height: 400px;
  }
}
</style>