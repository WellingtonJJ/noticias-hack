<template>
  <div class="main">
    <div class="principal">
      <h1>
        <a v-bind:href="link" target="_blank">Notícia: {{ title }}</a>
      </h1>
    </div>
    <div class="details">
      <h3>Autor: {{ author }}</h3>
      <h4>Pontuação: {{ score }}</h4>
    </div>

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
        })
        .catch((err) => {
          console.log(err);
          
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
  align-items: center;
  background-color: rgb(238, 236, 236);
  color: rgb(129, 126, 126);
  padding: 20px;
  margin: 18px 8px;
  max-width: 400px;
  min-width: 200px;
  border-radius: 30px;
}

a {
  text-decoration: none;
  color: #f16d00;
  font-size: 25px;
}

a:hover{
  color: #e28941;
  cursor: pointer;
}

h4{
  font-size: 15px;
}

.details{
  padding-top: 0;
}

.principal{
  min-height: 150px;
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
