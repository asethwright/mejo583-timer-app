<template>
  <div class="Timer">
    <p class="Timer-seconds">{{ seconds }} seconds</p>

    <h3 class="Timer-text">{{ text }}</h3>

    <div class="Timer-btn">Stop</div>
  </div>
</template>

<script>
export default {

  mounted () {
    console.log('Timer -> mounted.')
  },

  beforeDestroy () {
    console.log('Timer -> beforeDestroy.')
  },

  data () {
    return {
      seconds: 0,
      text: 'Test'
    }
  }
}
</script>

<style scoped>
.Timer {
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

.Timer-btn {
  display: block;
  margin: 0 auto;
  width: 50px;
  text-align: center;
  padding: 12px 18px;
  border-radius: 12px;
  color: #fff;
  background: rgb(50, 186, 250);
}
</style>
