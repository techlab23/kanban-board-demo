<template>
  <div id="app">
    <Board></Board>
  </div>
</template>

<script>
import Board from './components/Board.vue'
export default {
  name: 'app',
  components: {
    Board
  }
}
</script>

<style>
#app {
  margin-top:20px;
}
</style>
