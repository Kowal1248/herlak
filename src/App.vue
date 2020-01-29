<template>
  <div id="app">
    <nav class="navbar navbar-dark fixed-top bg-dark flex-md-nowrap p-0 shadow">
      <a class="navbar-brand col-sm-3 col-md-2 mr-0" href="#">Herlak Team</a>
    </nav>
    <main class="col-md-12 ml-sm-auto col-lg-12 px-4">
      <Table />
    </main>
  </div>
</template>

<script>
  import Table from './components/Table.vue'

  export default {
    name: 'app',
    components: {
      Table
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
