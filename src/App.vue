<template>
  <div id="app">
    <div class="container">
      <transition name="fade">
        <h1 v-if="showGreet">Пройти короткий тест на знание JS.</h1>
      </transition>
      <Test />
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
.fade-enter-active, .fade-leave-active {
  transition: opacity .3s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>