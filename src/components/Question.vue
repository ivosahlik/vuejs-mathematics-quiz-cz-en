<template>
  <div class="panel panel-default">
    <div class="panel-heading">
      <h3 class="panel-title text-center">{{ question }}</h3>
    </div>
    <div class="panel-body">
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg btn-margin" @click="">Result</button>
      </div>
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg btn-margin" @click="">Result</button>
      </div>
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg btn-margin" @click="">Result</button>
      </div>
      <div class="col-xs-12 col-sm-6 text-center">
        <button class="btn btn-primary btn-lg btn-margin" @click="">Result</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Question',
  data () {
    return {
      question: 'question'
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
