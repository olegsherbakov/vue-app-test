<template>
  <div id="app">
    <div class="container">
      <div class="flex-container">
        <div class="content">
          <h1 v-bind:class="{
            center: true,
            fadeOut: true,
            transparent: !showGreet
          }">
            Короткий тест на знание JS.
          </h1>
          <Test />
        </div>
      </div>
      <div class="footer">
        <div class="footer-content">
          Powered by <a href="https://vuejs.org/">Vue.js</a> 2018
          <br />Repository <a href="https://github.com/olegsherbakov/vue-app-test">github.com</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Test from './components/Test.vue'

export default {
  name: 'app',
  data: function() {
    return {
      showGreet: true,
    }
  },
  components: {
    Test,
  },
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html,
body,
#app,
.container {
  height: 100%;
}
html {
  font: 112.5%/1.45em georgia, serif;
}
body {
  font-family: georgia, serif;
  font-weight: 400;
  font-kerning: normal;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
h1 {
  padding: 1rem 0;
}
h3 {
  padding-bottom: 1rem;
}
code {
  display: block;
  font-size: 1.2rem;
}
.container {
  display: flex;
  flex-direction: column;
}
.flex-container {
  flex: 1 0 auto;
}
.content {
  max-width: 670px;
  min-width: 420px;
  margin: 0 auto;
  padding: 0 24px;
}
.footer {
  text-align: center;
  white-space: nowrap;
}
.footer-content {
  max-width: 670px;
  min-width: 420px;
  margin: 0 auto;
  padding: 24px;
  overflow: hidden;
  text-overflow: ellipsis;
}
.fadeOut {
  transition: opacity 0.7s ease-in 1s;
}
.transparent {
  opacity: 0.1;
}
.center {
  text-align: center;
}
.button {
  background: firebrick;
  color: white;
  border: none;
  box-shadow: 0 0 10px black;
  outline: none;
  cursor: pointer;
}
</style>
