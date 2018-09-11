<template>
  <div class="item">
    <b>Q:</b> {{ text }}
    <div class="values">
      <div
        class="value"
        v-for="(question, index) in values"
        :key="index"
      >
        <input
          class="input"
          type="radio"
          v-model="picked"
          v-bind:value="index"
          v-bind:name="`js-question` + index"
          v-bind:id="`js-question-` + index"
        />
          <label
            class="label"
            v-bind:for="`js-question-` + index"
          >
            {{ question.text }}
          </label>
      </div>
    </div>
    <button
      class="submit"
      v-on:click="submitResult"
      :disabled="picked === -1"
    >
      Ответить
    </button>
  </div>
</template>

<script>
export default {
  name: 'Question',
  data: function() {
    return {
      picked: -1
    }
  },
  props: ['text', 'values'],
  methods: {
    submitResult: function() {
      this.$parent.takeResult(this.picked)
      this.picked = -1
    }
  }
}
</script>

<style scoped>
.item {
  padding: 13px;
  border: 1px solid #ccc;
  border-radius: 10px;
  margin: 13px 0;
}
.input {
  position: relative;
  top: 1px;
}
.values {
  padding: 13px 0;
}
.value {
 padding: 7px 0;
}
.submit {
  padding: 3px;
  font-size: 17px;
}
</style>