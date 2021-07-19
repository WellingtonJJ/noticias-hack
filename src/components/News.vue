<template>
  <div class="main">
    <h1>
      <a v-bind:href="link" target="_blank">Título: {{ title }}</a>
    </h1>
    <h3>Autor: {{ author }}</h3>
    <h4>Pontuação: {{ score }}</h4>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "News",

  props: {
    newID: Number,
  },

  data() {
    return {
      baseURL: "https://hacker-news.firebaseio.com/v0/item/",
      title: "",
      author: "",
      score: "",
      link: "",
    };
  },

  methods: {
    findNotice() {
      let URL = `${this.baseURL}${this.newID}.json`;
      axios
        .get(URL)
        .then((res) => {
          this.title = res.data.title;
          this.author = res.data.by;
          this.score = res.data.score;
          this.link = res.data.url;
          // console.log("retorno get",this.link)
        })
        .catch((err) => {
          console.log(err);
          //TODO tratar erro de requisição
        });
    },
  },

  created() {
    this.findNotice();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  background-color: white;
}

a {
  text-decoration: none;
  color: black;
}

/*
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: white;
} */
</style>
