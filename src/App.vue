<template>
  <div class="container">
    <div class="row">
      <div>
        <h1 class="text-center">The mathematics quiz</h1>
      </div>
    </div>

    <div class="row">
      <div>
        <transition name="flip" mode="out-in">
          <component v-bind:is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'"></component>
        </transition>
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
  .flip-enter {
    /*transform: rotateY(0deg);*/
  }

  .flip-enter-active {
    animation: flip-in  0.5s ease-out forwards;
  }

  .flip-leave {
    /*transform: rotateY(0deg);*/
  }

  .flip-leave-active {
    animation: flip-out 0.5s ease-out forwards;
  }

  @keyframes flip-out {
    from {
      transform: rotateY(0deg);
    }
    to {
      transform: rotateY(90deg);
    }
  }

  @keyframes flip-in {
    from {
      transform: rotateY(90deg);
    }
    to {
      transform: rotateY(0deg);
    }
  }
</style>
