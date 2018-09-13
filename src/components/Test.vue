<template>
    <div class="container">
      <div class="center">
        <button
          class="button get-started"
          @click="begin"
          v-if="phase === 'begin'"
        >
          Начать тест
        </button>
      </div>
      <div v-if="phase === 'during'">
        <Progress
          v-bind:current="step"
          v-bind:length="questions.length"
        />
        <Question
          v-bind:step="step"
          v-bind:text="current.text"
          v-bind:values="current.values"
        />
      </div>
      <div v-if="phase === 'end'">
        <div class="center">
          <h3>Ваш результат: {{ calculate }} / {{ questions.length }}</h3>
          <button
            class="button get-repeat"
            @click="repeat"
          >
            Повторить тест
          </button>
        </div>
      </div>
    </div>
</template>

<script>
import data from '../assets/data'
import Question from './Question.vue'
import Progress from './Progress.vue'

export default {
  name: 'Test',
  data: function() {
    return {
      ...data,
      result: [],
    }
  },
  methods: {
    begin: function() {
      this.step += 1
      this.$parent.showGreet = false
    },
    takeResult(index) {
      this.result.push(this.current.values[index].right)
      this.step += 1
    },
    repeat: function() {
      this.result = []
      this.step = 1
    },
  },
  computed: {
    phase: function() {
      if (this.step === 0) {
        return 'begin'
      } else if (this.step !== 0 && this.step - 1 === this.questions.length) {
        return 'end'
      }
      return 'during'
    },
    current: function() {
      return this.questions[this.step - 1]
    },
    calculate: function() {
      return this.result.filter(r => r).length
    },
  },
  components: {
    Question,
    Progress,
  },
}
</script>

<style scoped>
.get-started,
.get-repeat {
  padding: 13px;
  border-radius: 10px;
  font-size: 21px;
}
</style>
