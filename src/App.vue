<template>
  <div id="app">
    <h1>Vejas as noticias:</h1>
    <h3>Visualizando atualmente {{ viewItems }} de {{totalItems}} notícias</h3>

    <input type="button" value="Exibir 10" v-on:click="findNewsIDs(10)"/>
    <input type="button" value="Exibir 20" v-on:click="findNewsIDs(20)"/>
    <input type="button" value="Exibir 30" v-on:click="findNewsIDs(30)"/>

    <News
      v-for="notice in newsIDs"
      :key="notice"
      id="news"
      v-bind:newID="notice"
    />
  </div>
</template>

<script>
import axios from "axios";
import News from "./components/News.vue";


export default {
  name: "App",

  components: {
    News,
  },

  data() {
    return {
      baseURL: "https://hacker-news.firebaseio.com/v0/topstories.json",
      newsIDs: [],
      viewItems: 0,
      totalItems: 0,
    };
  },

  methods: {
    findNewsIDs(itemsQuantity) {
      this.viewItems = itemsQuantity;

      axios
        .get(this.baseURL)
        .then((res) => {
          this.totalItems = res.data.length
          this.newsIDs = res.data.filter((el, i) => {
            return i < itemsQuantity;
          });
        })
        .catch((err) => {
          //TODO tratar erro de requisição
          console.log(err);
        });
    },
  },

  created() {
    this.viewItems = 10;
    this.findNewsIDs(this.viewItems);
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  background-color: dodgerblue;
}

#news {
  border: 10px black solid;
}
</style>
