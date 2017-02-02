<template>
  <div id="app">
    <!-- Form Component goes here -->

    <Timer></Timer>
  </div>
</template>

<script>
import Timer from './components/Timer'

export default {
  name: 'app',

  mounted () {
    console.log('App -> mounted.')
  },

  components: {
    Timer
  }
}
</script>

<style>
html, body {
  min-height: 100%;
}

body {
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Roboto', sans-serif;
  background: linear-gradient(to bottom right, #c8c897, #6590A2);
}

[v-cloak] { display:none; }

#app {

}
</style>
