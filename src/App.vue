<template>
  <div class="buttons">
    <TimerButton @click="startTimer(20,0)"> 00:20 </TimerButton>
    <TimerButton @click="startTimer(0,1)"> 1 minute </TimerButton>
    <TimerButton @click="startTimer(0,10)"> 10 minutes </TimerButton>
    <TimerButton @click="startTimer(0,45)"> 45 minutes</TimerButton>
    <TimerButton @click="startTimer(0,60)"> 1 hour</TimerButton>
  </div>
  <Timer :isStarted="isStarted" :seconds="seconds" :minutes="minutes" />

</template>

<script>
import TimerButton from '@/components/UI/TimerButton.vue'
import Timer from '@/components/Timer.vue'

export default {
  name: 'App',
  components: { Timer, TimerButton },
  data() {
    return {
      isStarted: false,
      seconds: 0,
      minutes: 0,

    }
  },
  methods: {
    startTimer(s, m) {
      this.seconds = s;
      this.minutes = m;
      this.isStarted = true
    },
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.buttons {
  display: flex;
}

#app {
  background-color: teal;
  height: 100vh;
}

</style>
