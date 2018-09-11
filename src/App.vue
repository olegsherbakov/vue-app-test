<template>
  <div id="app">
    <div class="container">
      <h1>Здесь Вы можете пройти тест на знание JS.</h1>
      <Test />
    </div>
  </div>
</template>

<script>
import Test from './components/Test.vue'

export default {
  name: 'app',
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
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
h1 {
  margin: 26px 0;
}
.container {
  width: 600px;
  text-align: left;
  margin: 0 auto;
}
</style>
