<script setup lang="ts">
import { ref } from "vue";
import Btn from "./Btn.vue";

const time = ref(1500);
let progressInterval: ReturnType<typeof setInterval>;

const startTimmer = () => {
  progressInterval = setInterval(() => {
    time.value--;
    
    if (time.value === 0) {
      clearInterval(progressInterval);
      time.value = 1500;
    }
    
  }, 1000);
};


const restartTimmer = () => {
  
};
</script>

<template>
  <div class="timmer">
    <h1 class="title">Pomodoro Rd 1</h1>
    <div class="time">
      <span>25 : 00</span>
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
}

.btns {
  display: flex;
  align-items: center;
  gap: 20px;
  margin: 0 auto;
}
</style>
