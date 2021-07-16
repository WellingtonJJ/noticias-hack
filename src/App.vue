<template>
  <div id="app">
    <h1>Descubra novas Notícias</h1>
    <div class="grupo">
      <Noticiar noticiaA="8863"/>
      <Noticiar noticiaA="9038733"/>
      <Noticiar noticiaA="9129199"/>
    </div>
    <div class="grupo">
      <Noticiar noticiaA="9127761"/>
      <Noticiar noticiaA="9128141"/>
      <Noticiar noticiaA="9128264"/>
    </div>
    <div class="grupo">
      <Noticiar noticiaA="9127792"/>
      <Noticiar noticiaA="9129248"/>
      <Noticiar noticiaA="9127092"/>
    </div>
    <div class="grupo">
      <Noticiar noticiaA="9128367"/>
      <Noticiar noticiaA="9038733"/>
      <Noticiar noticiaA="27849412"/>
    </div>
  </div>
</template>

<script>
import Noticiar from "./components/Noticiar.vue";
export default {
  name: "Home",
  components: {
     Noticiar
  },
};
    
</script>

<style>
/*

/* ==========================================================================
   Reset
   ========================================================================== */

/**
 * Remove anchor text-decoration
 */

a {
  text-decoration: none;
}

/**
 * Remove list-style
 */

ol,
ul {
  list-style: none;
}

html,
body,
div,
span,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
a,
em,
img,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
article,
footer,
header,
nav,
section,
main {
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
}

h2,
h3,
h4,
h5,
h6,
p,
a,
ul {
  font-size: 1em;
  font-weight: normal;
}



#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #da5306;background: #111111;
}

.grupo{
  display: flex;
  flex-wrap: wrap;
}

h1{
  padding: 40px;
  color: aliceblue;
}

h2{
  font-size: 26px;
}

</style>
