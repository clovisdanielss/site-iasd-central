<template>
  <form class="my-modal col-md-12 card border m-auto p-3">
    <div class="row">
      <div class="col">
        <h1>Adicionar Notícia</h1>
        <div class="icon" @click.prevent="onClose">
          <i class="fas fa-times" @click.prevent="onClose"></i>
        </div>
        <hr />
      </div>
    </div>
    <div class="row">
      <div class="col-xl-8">
        <div class="input-group mb-3">
          <div class="input-group-prepend">
            <span class="input-group-text" id="basic-addon1">Título</span>
          </div>
          <input
            type="text"
            class="form-control"
            placeholder="Título da Notícia"
            aria-label="title"
            aria-describedby="basic-addon1"
            v-model="newsToAppend.header"
          />
        </div>
      </div>
      <div class="col-xl-4">
        <div class="input-group mb-3">
          <div class="input-group-prepend">
            <span class="input-group-text" id="basic-addon1">Link da Imagem</span>
          </div>
          <input
            type="text"
            class="form-control"
            placeholder="https://exemplo.com/imagem.png"
            aria-label="image"
            aria-describedby="basic-addon1"
            v-model="newsToAppend.image"
          />
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-xl">
        <div class="input-group mb-3">
          <div class="input-group-prepend">
            <span class="input-group-text" id="basic-addon1">Palavras-Chave</span>
          </div>
          <input
            type="text"
            class="form-control"
            placeholder="Calebe, Missão, Culto JA,"
            aria-label="tags"
            aria-describedby="basic-addon1"
            v-model="newsToAppend.tags"
          />
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-xl">
        <div class="input-group">
          <div class="input-group-prepend">
            <span class="input-group-text">Texto da Notícia</span>
          </div>
          <textarea
            v-model="newsToAppend.text"
            class="form-control mh-500"
            aria-label="With textarea"
          ></textarea>
        </div>
      </div>
    </div>
    <button
      v-on:click.prevent="onSubmit"
      type="submit"
      class="btn btn-secondary btn-lg btn-block mt-3"
    >Adicionar</button>
  </form>
</template>

<script>
export default {
  name: "EditHomeComponent",
  data() {
    return {
      newsToAppend: {
        header: "",
        tags: "",
        date: new Date(),
        text: ``,
        image: ""
      }
    };
  },
  methods: {
    onSubmit() {
      this.submit(this.newsToAppend);
      this.newsToAppend = {
        header: "",
        tags: "",
        date: new Date(),
        text: ``,
        image: ""
      };
    }
  },
  props: {
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
  .mh-500{
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
  .mh-500{
    min-height: 400px;
  }
}
</style>