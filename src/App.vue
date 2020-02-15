<template>
  <div id="app">
    <TheHeader />
    <main class="main">
      <router-view />
    </main>
    <TheFooter />
  </div>
</template>
<script>
import TheHeader from "./components/TheHeader.vue";
import TheFooter from "./components/TheFooter.vue";
export default {
  name: "app",
  components: {
    TheHeader,
    TheFooter
  }
};
</script>
<style>
@import url("https://fonts.googleapis.com/css?family=Roboto:100,100i,300,300i,400,400i,500,500i,700,700i,900,900i&display=swap");
/* RESET-KAWEY - CSS */
* {
  box-sizing: border-box;
}
body,
input,
table,
td,
th,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
cite,
img,
span,
a {
  padding: 0;
  margin: 0;
  border: 0;
  box-sizing: border-box;
  font-style: normal;
}
ul,
li {
  list-style: none;
}
a {
  text-decoration: none;
  color: #345;
}
img {
  max-width: 100%;
  display: block;
}
body {
  font-family: "Roboto", sans-serif;
  color: #345;
  background: url("./assets/pattern.svg") repeat top;
}

/* STYLES GLOBAIS */
#app {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}
.main {
  flex: 1;
}
.btn {
  display: block;
  padding: 10px 30px;
  background: #87f;
  border-radius: 4px;
  color: #fff;
  text-align: center;
  font-size: 1rem;
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.2);
  transition: all 0.3s;
  border: none;
  font-family: "Roboto", sans-serif;
  cursor: pointer;
}
.btn:hover {
  background: #65d;
  transform: scale(1.1);
}

input,
textarea {
  border-radius: 4px;
  border: 1px solid #fff;
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.1);
  padding: 15px;
  transition: all 0.3s;
  font-size: 1rem;
  font-family: "Roboto", sans-serif;
  margin-bottom: 15px;
}
input:hover,
textarea:hover,
input:focus,
textarea:focus {
  outline: none;
  box-shadow: 0 6px 12px rgba(30, 60, 90, 0.2);
  border-color: #87f;
}
</style>
