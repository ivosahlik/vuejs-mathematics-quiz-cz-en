<template>
  <div class="container">
    <div class="row">
      <div>
        <h1 class="text-center">The mathematics quiz</h1>
      </div>
    </div>

    <div class="row">
      <div>
        <component v-bind:is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'"></component>
      </div>
    </div>
  </div>
</template>

<script>
import Question from './components/Question'
import Answer from './components/Answer'

export default {
  components: {
    appAnswer: Answer,
    appQuestion: Question
  },
  data () {
    return {
      mode: 'app-question'
    }
  },
  methods: {
    answered (isCorrect) {
      if (isCorrect) {
        this.mode = 'app-answer'
      } else {
        this.mode = 'app-question'
        alert('Wrong, try again!')
      }
    }
  }
}
</script>

<style lang="scss">

</style>
