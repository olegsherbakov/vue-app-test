<template>
  <div class="progress">
    <div
       v-for="step in length"
       v-bind:class="{ step: true, passed: (step < current), current: step === current }"
       :key="step"
    >
      {{ step }}
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Progress',
    props: ['current', 'length']
  }
</script>

<style scoped>
.progress {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 7px 0;
}
.step {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 30px;
  height: 30px;
  background: ivory;
  border-radius: 15px;
  margin: 0 7px;
  box-shadow: 0 0 5px #ccc;
  border: 1px solid #ccc;
  transition: opacity .3s ease-in,
    background-color .3s ease-out .3s,
    color .3s ease-out .3s;
}
.passed {
  opacity: .2;
}
.current {
  background: firebrick;
  color: ivory;
}
</style>