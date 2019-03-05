<template>
  <div id="app">
    <div class="ui inverted segment">
      <div class="ui inverted secondary pointing menu">
        <a class="item active">
          App conectada a la api de Giphy
        </a>
      </div>
    </div>
    <div class="ui container">
      <test></test>
    </div>
  </div>
</template>

<script>
import test from './components/test.vue'

export default {
  name: 'app',
  components: {
    test
  }
}
</script>

<style lang="sass">
  @import "~semantic-ui/dist/semantic.min.css"
  body
    background-color: grey
</style>
