<template>
  <div id="app">
    <div class="container">
      <div class="flex-container">
        <div class="content">
          <h1 v-bind:class="{
            center: true,
            fadeOut: true,
            transparent: !showGreet
          }">Короткий тест на знание JS.</h1>
          <Test />
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
      showGreet: true
    }
  },
  components: {
    Test
  }
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
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
h1 {
  padding: 26px 0;
}
h3 {
  padding: 0 0 13px;
}
h4 {
  padding: 13px 0;
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
  margin: 0 auto;
  padding: 0 24px;
}
.fadeOut {
  transition: opacity .7s ease-in 1s;
}
.transparent {
  opacity: .1;
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