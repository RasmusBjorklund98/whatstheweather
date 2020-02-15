<template>
  <div id="app">
    <main>
    <Search/>
    </main>
  </div>
</template>

<script>
import Search from './components/Search.vue'

export default {
  name: 'App',
  components: {
    Search
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}

#app {
  background-color: blueviolet;
}

main {
  min-height: 100vh;
  padding: 25px;
}
</style>
