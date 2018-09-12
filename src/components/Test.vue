<template>
  <div class="container">
    <div class="center">
      <button
        class="get-started"
        @click="begin"
        v-if="phase === 'begin'"
      >
        Начать тест
      </button>
    </div>
    <div v-if="phase === 'during'">
      <b>Вопрос #{{ step }}</b>
      <Question
        v-bind:text="current.text"
        v-bind:values="current.values"
      />
      <Progress
         v-bind:current="step"
         v-bind:length="questions.length"
      />
    </div>
    <div v-if="phase === 'end'">
      <div class="center">
        <h1>Ваш результат: {{ calculate }} / {{ questions.length }}</h1>
        <button
          class="get-repeat"
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
      result: []
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
    }
  },
  computed: {
    phase: function() {
      if (this.step === 0) {
        return 'begin'
      } else if ((this.step !== 0) && ((this.step - 1) === this.questions.length)) {
        return 'end'
      }
      return 'during'
    },
    current: function() {
      return this.questions[this.step - 1]
    },
    calculate: function() {
      return this.result.filter(r => r).length
    }
  },
  components: {
    Question,
    Progress
  }
}

</script>

<style scoped>
.container {
  padding: 26px 0;
}
.center {
  text-align: center;
}
.get-started, .get-repeat {
  background: firebrick;
  padding: 13px;
  color: white;
  border: none;
  border-radius: 10px;
  box-shadow: 0 0 10px black;
  outline: none;
  cursor: pointer;
  font-size: 21px;
}
</style>
