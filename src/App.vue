<template>
  <div id="app">
    <!-- Form Component goes here -->
    <TimerForm></TimerForm>
    <Timer
      v-for="(timer, index) in timers"
      :key="timer.id"
      :timer="timer"
      @stop="stopped(index)"
    ></Timer>
  </div>
</template>

<script>
import TimerForm from './components/TimerForm'
import Timer from './components/Timer'

export default {
  name: 'app',

  data () {
    return {
      timerid: 0,
      timers: []
    }
  },

  mounted () {
    console.log('App -> mounted.')
    this.$evt.$on('add', this.formSubmitted)
  },

  beforeDestroy () {
    this.$evt.$off('add', this.formSubmitted)
  },

  components: {
    TimerForm,
    Timer
  },

  methods: {
    stopped (i) {
      this.timers.splice(i, 1)
    },

    formSubmitted (data) {
      console.log('App -> formSubmitted', data)
      this.timerid++

      this.timers.push({
        id: this.timerid,
        seconds: data.seconds,
        text: data.text
      })
    }
  }
}
</script>

<style>
html, body {
  min-height: 100%;
}

body {
  margin: 0;
  font-family: 'Roboto', sans-serif;
  background: linear-gradient(to bottom right, #c8c897, #6590A2);
}

[v-cloak] { display:none; }

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}
.fade-enter, .fade-leave-to {
  opacity: 0
}
</style>
