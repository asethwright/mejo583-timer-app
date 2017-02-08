<template>
  <div id="app">
    <!-- Form Component goes here -->
    <TimerForm></TimerForm>
    <transition name="fade">
      <Timer
        v-for="timer in timers"
        :timer="timer"
        @stop="stopped"
      ></Timer>
    </transition>
  </div>
</template>

<script>
import TimerForm from './components/TimerForm'
import Timer from './components/Timer'

export default {
  name: 'app',

  data () {
    return {
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
    stopped (t) {
      this.timers.splice(this.timers.indexOf(t), 1)
    },

    formSubmitted (data) {
      console.log('App -> formSubmitted', data)

      this.timers.push({
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
