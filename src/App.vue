<template>
  <div id="app">
    <main>
      <!-- <h1>WHAT'S <br> THE <br> WEATHER?</h1> -->
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
  font-family: "Futura", serif;
}

#app {
  background-color: #32328E;
  /*  */
}

main {
  min-height: 100vh;
  padding: 25px;
}

h1 {
  font-size: 3rem;
  color: white;
}

h5 {
  color: white; 
}
</style>
