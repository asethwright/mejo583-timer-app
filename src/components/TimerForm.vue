<template>
  <div class="TimerForm">
    <p>
      <label>How long?</label>
      <input type="number" v-model="seconds" />
    </p>

    <p>
      <label>What for?</label>
      <input type="text" v-model="purpose" />
    </p>

    <div class="btn" @click="add">Start</div>
  </div>
</template>

<script>
export default {

  data () {
    return {
      seconds: 10,
      purpose: ''
    }
  },

  methods: {
    add () {
      console.log('TimerForm -> add')
      this.$evt.$emit('add', {
        seconds: this.seconds,
        text: this.purpose
      })
      this.reset()
    },

    reset () {
      this.seconds = 10
      this.purpose = ''
    }
  }

}
</script>

<style>
.TimerForm {
  margin: 20px;
  float: left;
  padding: 20px;
  color: rgb(50, 186, 250);
  background-color: rgb(30, 56, 76);
  border-radius: 5px;
  height: 310px;
  width: 210px;
}

.TimerForm label {
  display: block;
  margin-bottom: 5px;
}

.TimerForm input {
  width: 100%;
  box-sizing: border-box;
  padding: 8px 14px;
  border: 1px solid rgb(50, 186, 250);
  border-radius: 5px;
  font-size: 16px;
  color: #5a5a5a;
}

.TimerForm p:first-child {
  margin-top: 0;
}
</style>
