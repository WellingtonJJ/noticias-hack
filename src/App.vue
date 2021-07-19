<template>
  <div id="app">
    <div class="header">
      <h1>Hack News</h1>
      <h3>Visualizando atualmente {{ viewItems }} notícias</h3>
    </div>


    <input class="btn" type="button" value="Exibir 10" v-on:click="findNewsIDs(10)"/>
    <input class="btn" type="button" value="Exibir 20" v-on:click="findNewsIDs(20)"/>
    <input class="btn" type="button" value="Exibir 30" v-on:click="findNewsIDs(30)"/>
    <div class="newsView">
      <News
        v-for="notice in newsIDs"
        :key="notice"
        id="news"
        v-bind:newID="notice"
      />
    </div>
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
  /*text-align: center;
  color: #2c3e50;*/
}

body {
  background-color: rgb(255, 255, 255);
  word-wrap: break-word;
  word-break: break-all;
  text-align-last: center;
}

.btn{
    background-color: #f16d00; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 2px;
    cursor: pointer;
}

.btn:hover{
  background-color: rgb(51, 50, 50);
  color: white;
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
}

#news {
  border: 0px black solid;
}

.newsView {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
}

.header {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}



</style>
