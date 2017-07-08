<template>
  <nav class="navbar">
    <div class="navbar-brand">
      <a class="navbar-item" href="/"> 
        <h2 class="title brand-word">K</h2> { Kanban Board Demo }
      </a>
      <div class="navbar-burger burger" data-target="navMenuExample">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </nav>
</template>
<script>
  export default {}
</script>
<style>
  .navbar {
    background-color:#f5f5f5;
    margin-top:0px;
  }
  .brand-word {
    color: #2196f3;
    font-size: 3rem;
    font-weight: 600;
    padding-right:20px;
  }
  .navbar-item {
    font-weight: 600;
  }
</style>