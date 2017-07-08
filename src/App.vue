<template>
  <div class="container-fluid">
    <Navigation></Navigation>
    <Board></Board>
  </div>
</template>
<script>
  const Navigation = () => import('./components/Navigation.vue')
  const Board = () => import('./components/Board.vue')
  export default {
    name: 'app',
    components: {
      Board, Navigation
    }
  }
</script>
<style>
</style>
