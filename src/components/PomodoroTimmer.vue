<script setup lang="ts">
import { ref } from "vue";
import Btn from "./Btn.vue";

const time = ref(1500);
let progressInterval: ReturnType<typeof setInterval>;
let min = ref("25");
let sec = ref("00");

const startTimmer = () => {
  progressInterval = setInterval(() => {
    time.value--;

    if (time.value === 0) {
      clearInterval(progressInterval);
      time.value = 1500;
    }
    NumbertoString(time.value);
  }, 1000);
};
const NumbertoString = (number: number) => {
  const minutes = Math.trunc(number / 60)
    .toString()
    .padStart(2, "0");
  const seconds = Math.trunc(number % 60)
    .toString()
    .padStart(2, "00");
  min.value = minutes;
  sec.value = seconds;
};

const restartTimmer = () => {
  clearInterval(progressInterval);
  time.value = 1500;
  min.value = "25";
  sec.value = "00";
};
</script>

<template>
  <div class="timmer">
    <h1 class="title">Pomodoro Rd 1</h1>
    <div class="time">
      <span>{{ min }}</span>
      <span>:</span>
      <span>{{ sec }}</span>
    </div>
    <div class="btns">
      <Btn variation="primary" @click="startTimmer">Start ▶︎</Btn>
      <Btn variation="primary" @click="restartTimmer">Restart ⟳</Btn>
    </div>
  </div>
</template>

<style>
.timmer {
  display: flex;
  flex-direction: column;
  gap: 60px;
  width: fit-content;
  margin: 100px auto;
  justify-content: center;
}
.title {
  font-size: 6rem;
  color: white;
  text-transform: uppercase;
  font-family: Arial, Helvetica, sans-serif;
}
.time {
  font-family: Arial, Helvetica, sans-serif;
  color: white;
  font-size: 17rem;
  font-weight: 700;
  margin: 0 auto;
}
.btns {
  display: flex;
  align-items: center;
  gap: 20px;
  margin: 0 auto;
}
</style>
