<template>
  <div class="panel panel-default">
    <div class="panel-heading">
      <h3 class="panel-title text-center">{{ question }}</h3>
    </div>
    <div class="panel-body">
      <div class="col-xs-12 col-sm-6 text-center" v-for="n in COUNT_LOOP" :key="n">
        <button class="btn btn-primary btn-lg btn-margin" @click="onAnswer(n)">{{resultNum(n)}}</button>
      </div>
    </div>
  </div>
</template>

<script>
const MODE_ADDITION = 1
const MODE_SUBTRACTION = 2
const MODE_MULTIPLE = 3
const NUMBER_MAX = 100
const NUMBER_MIN = 1

export default {
  name: 'Question',
  data () {
    return {
      question: 'Oops, an error ocurred :/',
      COUNT_LOOP: 4,
      MODE_MAX: 3,
      MODE_MIN: 1,
      btnData: [
        { correct: true, answer: 0 },
        { correct: false, answer: 0 },
        { correct: false, answer: 0 },
        { correct: false, answer: 0 }
      ]
    }
  },

  created () {
    this.generateQuestion()
  },

  methods: {

    generateQuestion () {
      const firstNum = this.generateRandomNumber(NUMBER_MIN, NUMBER_MAX)
      const secondNum = this.generateRandomNumber(NUMBER_MIN, NUMBER_MAX)
      const modeNum = this.generateRandomNumber(this.MODE_MIN, this.MODE_MAX)

      let correctAnswer = 0

      switch (modeNum) {
        case MODE_ADDITION:
          correctAnswer = firstNum + secondNum
          this.question = `What's ${firstNum} + ${secondNum}?`
          break
        case MODE_SUBTRACTION:
          correctAnswer = firstNum - secondNum
          this.question = `What's ${firstNum} - ${secondNum}?`
          break
        case MODE_MULTIPLE:
          correctAnswer = firstNum * secondNum
          this.question = `What's ${firstNum} * ${secondNum}?`
          break
        default:
          correctAnswer = 0
          this.question = 'Oops, an Error occurred :/'
      }

      for (var i = 0; i < this.COUNT_LOOP; i++) {
        this.btnData[i].answer = this.generateRandomNumber(correctAnswer - 10, correctAnswer + 10, correctAnswer)
        this.btnData[i].correct = false
      }

      const correctButton = this.generateRandomNumber(0, this.MODE_MAX)
      this.btnData[correctButton].correct = true
      this.btnData[correctButton].answer = correctAnswer
    },

    onAnswer (n) {
      var isCorrect = this.btnData[n - 1].correct
      this.$emit('answered', isCorrect)
    },

    generateRandomNumber (min, max) {
      const randomNumber = Math.round(Math.random() * (max - min) + min)
      return randomNumber
    },

    resultNum (n) {
      return this.btnData[n - 1].answer
    }

  }

}
</script>

<style lang="scss">

  .btn-margin {
    margin: 10px;
  }

  .panel-heading {
    border-left: 1px solid transparent;
  }

</style>
