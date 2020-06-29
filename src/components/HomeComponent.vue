<template>
  <div id="home-component" class="row">
    <EditHomeComponent v-if="edit" :submit="submit" :onClose="onClose"></EditHomeComponent>

    <div v-if="selected !== null" class="container-xl">
      <div class="col blog-main mt-3">
        <div class="blog-post">
          <a class="news-unselect" @click.prevent="onUnselect" href="#">Voltar</a>

          <h2 class="blog-post-title">{{newsArray[selected].header}}</h2>
          <hr />
          <p class="blog-post-meta">
            {{newsArray[selected].date}}
            <br />
            <a href="#">{{newsArray[selected].tags.join(" ")}}</a>
          </p>
          <div class="news-text">
            <img
              v-bind:src="newsArray[selected].image"
              width="200px"
              height="200px"
              class="rounded float-left mr-3"
            />
            <p
              class="text-justify"
              v-for="(text,index) in newsArray[selected].text.split('>')"
              :key="index"
            >{{text}}</p>
          </div>
          <hr />
        </div>
      </div>
    </div>
    <div v-else id="home-component-news" class="col">
      <div class="col mt-3">
        <h1>Notícias</h1>
        <hr />
      </div>
      <div class="news-container">
        <div
          v-for="(news,index) in newsArray"
          :key="index"
          class="news no-gutters border rounded overflow-hidden mb-4 shadow-sm h-md-250 position-relative"
        >
          <div class="col-md-8 p-4 d-flex flex-column position-static">
            <strong class="d-inline-block mb-2 text-primary">{{news.tags.join(" ")}}</strong>
            <h3 class="mb-0">{{news.header}}</h3>
            <div class="mb-1 text-muted">{{news.date}}</div>
            <p class="card-text mb-auto">{{news.text.substr(0,40) + " ..."}}</p>
            <a @click.prevent="onSelect(index)" href="#" class="stretched-link">Continue lendo</a>
          </div>
          <div class="col-4 d-none d-lg-block">
            <img v-bind:src="news.image" width="100%" height="100%" fill="#55595c" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import EditHomeComponent from "../components/EditHomeComponent.vue";

export default {
  data() {
    return {
      selected: null,
      edit: false,
      newsArray: [
        {
          header: "Iniciativa de criação de site na IASD Central de Fortaleza",
          tags: ["Comunicação", "Site"],
          date: new Date(),
          text: `A inciativa foi tomada na comissão do dia 23/06/2020. 
            Foi tomado então o esqueleto do projeto existente e tomado como base para construção do novo site`,
          image:
            "https://i.pinimg.com/originals/56/9a/dd/569add31abfa91769d824346e2b2346b.jpg"
        }
      ]
    };
  },
  mounted() {
    console.log("Dados carregados aqui!");
    let urlSearch = new URLSearchParams(window.location.search);
    if (urlSearch.get("edit")) {
      this.edit = true;
    }
  },
  methods: {
    onClose() {
      console.log("Chamado!");
      this.edit = false;
    },
    onSelect(index) {
      this.selected = index;
    },
    onUnselect() {
      this.selected = null;
    },
    submit(news) {
      console.log("Enviar dados aqui");
      news.tags = news.tags.split(",");
      this.newsArray.push(news);
      news = {
        header: "",
        tags: "",
        date: new Date(),
        text: ``,
        image: ""
      };
    }
  },
  watch: {
    newsToAppend: {
      header: (oldVal, newVal) => {
        console.log(newVal);
      }
    }
  },
  components: {
    EditHomeComponent
  },
  name: "HomeComponent"
};
</script>

<style scoped>
.news {
  display: inline-flex;
  width: 32%;
  margin: 10px;
  transition: width 2s;
}
.news-text > img,
.news-text > div > p {
  display: inline;
}
.news-unselect {
  float: right;
}

@media (max-width: 1280px) {
  .news {
    width: 50%;
    margin: 0px;
  }
}

@media (max-width: 720px) {
  .news {
    width: 100%;
    margin: 0px;
  }
}
</style>