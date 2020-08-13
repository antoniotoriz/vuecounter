<template>
  <div>
    {{ message }}
    <div id="timer">
      <span id="minutes">{{ minutes }}</span>
      <span id="middle">:</span>
      <span id="seconds">{{ seconds }}</span>
    </div>
    <div id="buttons">
      <button id="start" v-if="!timer" v-on:click="startTimer">START</button>
      <button id="stop" v-if="timer" v-on:click="stopTimer">STOP</button>
      <button id="reset" v-if="resetButton" v-on:click="resetTimer">RESET</button>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    timer: null,
    totalTime: 25 * 60,
    resetButton: false,
    message: "shall we begin?",
  }),
  computed: {
    minutes: function () {
      const minutes = Math.floor(this.totalTime / 60);
      return this.padTime(minutes);
    },
    seconds: function () {
      const seconds = this.totalTime - this.minutes * 60;
      return this.padTime(seconds);
    },
  },
  methods: {
    startTimer: function () {
      this.timer = setInterval(() => this.countdown(), 1000);
      this.resetButton = true;
      this.message = "DO WERK!";
    },
    stopTimer: function () {
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
      this.message = "shall we resume?";
    },
    resetTimer: function () {
      this.totalTime = 25 * 60;
      clearInterval(this.timer);
      this.timer = null;
      this.resetButton = false;
      this.message = "let's start over";
    },
    padTime: function (time) {
      return (time < 10 ? "0" : "") + time;
    },
    countdown: function () {
      if (this.totalTime >= 1) {
        this.totalTime--;
      } else {
        this.totalTime = 0;
        alert("TIMES UP!");
        this.resetTimer();
      }
    },
  },
};
</script>

<style scoped>
</style>
