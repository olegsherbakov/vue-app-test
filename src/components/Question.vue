<template>
  <div class="item">
    <h4>Q #{{ step }}</h4>
    <code>
      {{ text }}
    </code>
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
      class="button submit"
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
      picked: -1,
    }
  },
  props: ['step', 'text', 'values'],
  methods: {
    submitResult: function() {
      this.$parent.takeResult(this.picked)
      this.picked = -1
    },
  },
}
</script>

<style scoped>
.item {
  padding: 13px;
  border: 1px solid #ccc;
  border-radius: 13px;
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
  border-radius: 7px;
  padding: 7px;
  font-size: 17px;
}
</style>
