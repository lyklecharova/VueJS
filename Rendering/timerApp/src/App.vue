<script>
function parseTimerInput(text) {
  const [h, m, s] = text.split(':').map(num => Number(num));
  return s + 60 * m + 3600 * h;
}
export default {
  data() {
    return {
      userInput: '',
      time: 0,
      timerSeconds: 0,
      referenceSeconds: 0,
      showWarning: false,
      interval: null,
      isPaused: false,
    };
  },
  watch: {
    timerSeconds(newValue) {
      if (this.showWarning)
        return;

      if (newValue < this.referenceSeconds * 0.2) {
        this.showWarning = true;
      }
    },
  },
  methods: {
    onInput(event) {
      this.userInput = event.target.value;
    },
    onStart() {
      if (this.isPaused) {
        this.isPaused = false;
        this.handlerTimer();
        return;
      }

      this.timerSeconds = parseTimerInput(this.userInput);
      this.referenceSeconds = parseTimerInput(this.userInput);
      this.handlerTimer();
    },
    handlerTimer() {
      this.interval = setInterval(() => {
        if (this.timerSeconds > 0) {
          this.timerSeconds -= 1;
        }
        else {
          clearInterval(this.interval);
          this.interval = null;
          this.onReset();
        }
      }, 1000);
    },
    onPause() {
      if (this.interval) {
        clearInterval(this.interval);
        this.interval = null;
        this.isPaused = true;
      }
    },
    onReset() {
      if (this.interval) {
        clearInterval(this.interval);
        this.interval = null;
      }
      this.timerSeconds = 0;
      this.referenceSeconds = 0;
      this.userInput = '';
      this.showWarning = false;
      this.isPaused = false;
    },
  },
};
</script>

<template>
  <h1>My timer</h1>
  <input type="text" @input="onInput">
  <button type="button" @click="onStart">
    Start
  </button>
  <button type="button" @click="onPause">
    Pause
  </button>
  <button type="button" @click="onReset">
    Reset
  </button>

  <p v-if="timerSeconds">
    Remaining time {{ timerSeconds }}
  </p>
  <p v-if="showWarning">
    Less than 20% remaining
  </p>
</template>
