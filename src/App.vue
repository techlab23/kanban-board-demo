<template>
  <div id="app">
    <Navigation></Navigation>
    <Board class="board"></Board>
  </div>
</template>

<script>
const Board = () => import('./components/Board.vue')
const Navigation = () => import('./components/Navigation.vue')

export default {
  name: 'app',
  components: {
    Board,
    Navigation
  }
}
</script>

<style>
#app {
  margin-top:0px;
}
.board {
  padding-top:10px;
}
</style>
