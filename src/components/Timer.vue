<template>
  <div>
    <div class="timer">
      {{ timerMinutes > 9 ? timerMinutes : '0' + timerMinutes }}:{{
        timerSeconds > 9 ? timerSeconds : '0' + timerSeconds
      }}
    </div>
  </div>
</template>

<script>
export default {
  props: ['isStarted','seconds','minutes'],
  data() {
    return {
      totalSeconds: 0,
      timerSeconds:0,
      timerMinutes:0,
      intervalId: null,
    }
  },
  methods: {
    startTimer() {
      this.totalSeconds = this.minutes*60 + this.seconds;
      this.totalSeconds--;
      this.intervalId = setInterval(() => {
        if (this.totalSeconds >= 0) {
          this.timerMinutes = Math.trunc(this.totalSeconds / 60)
          this.timerSeconds = this.totalSeconds % 60
          this.totalSeconds--;
        }
      }, 1000)
    },
    stopTimer() {
      if (this.intervalId) {
        clearInterval(this.intervalId);
        this.intervalId = null;
      }
    },
    resetTimer() {
      this.stopTimer();
      this.timerMinutes = this.minutes;
      this.timerSeconds = this.seconds;
    }
  },

  mounted() {
    if (this.isStarted) {
       this.startTimer();
    }
  },
  watch: {
    isStarted(newVal) {
      if (newVal) {
        this.startTimer();
      } else {
        this.stopTimer();
      }
    },
    seconds(newVal, oldVal) {
      if (newVal !== oldVal) {
        this.resetTimer();
        if (this.isStarted) {
          this.startTimer();
        }
      }
    },
    minutes(newVal, oldVal) {
      if (newVal !== oldVal) {
        this.resetTimer();
        if (this.isStarted) {
          this.startTimer();
        }
      }
    }
  },
  beforeUnmount() {
    this.stopTimer();
  }
};

</script>

<style scoped>
.timer {
  margin-top: 30vh;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 280px;
}
</style>
