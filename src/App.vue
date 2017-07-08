<template>
  <div id="app">
    <div class="container-fluid">
      <Navigation></Navigation>
      <Board></Board>
    </div>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Board from './components/Board.vue'
export default {
  name: 'app',
  components: {
    Board, Navigation
  }
}
</script>

<style>
#app {
  /*margin-top:20px;*/
}
</style>
