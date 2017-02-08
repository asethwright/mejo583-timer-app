<template>
  <div class="Timer">
    <p class="Timer-seconds">{{ countdown }} seconds</p>

    <h3 class="Timer-text">{{ purpose }}</h3>

    <div class="Timer-btn">Stop</div>
  </div>
</template>

<script>
export default {

  mounted () {
    console.log('Timer -> mounted.')
    this.interval = setInterval(() => {
      this.tick()
    }, 1000)
  },

  beforeDestroy () {
    console.log('Timer -> beforeDestroy.')
    clearInterval(this.interval)
  },

  props: [
    'timer'
  ],

  data () {
    return {
      myName: 'seth',
      interval: 0,
      purpose: this.timer.text,
      countdown: this.timer.seconds
    }
  },

  methods: {
    tick () {
      this.countdown--
      if (this.countdown <= 0) {
        this.stop()
      }
    },

    stop () {
      console.log('Timer -> Stop')
      clearInterval(this.interval)
      this.$emit('stop', this.timer)
    }
  }

}
</script>

<style>
.Timer {
  float: left;
  margin: 20px;
  color: rgb(50, 186, 250);
  background-color: rgb(30, 56, 76);
  border-radius: 5px;
  height: 350px;
  width: 250px;
}

.Timer-seconds {
  text-align: center;
  padding: 20px 0;
  font-weight: 200;
  font-size: 1.3em;
}

.Timer-text {
  text-align: center;
  margin: 50px 0;
  font-size: 2em;
  font-weight: 400;
}

.Timer-btn,
.btn {
  display: block;
  margin: 0 auto;
  width: 50px;
  text-align: center;
  padding: 12px 18px;
  border-radius: 12px;
  color: #fff;
  background: rgb(50, 186, 250);
  cursor: pointer;
}

.Timer-btn:hover,
.btn:hover {
  background: rgba(50, 186, 250, 0.7);
}
</style>
