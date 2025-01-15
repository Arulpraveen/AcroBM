<template>
    <div v-if="show" class="screensaver" @click="hideScreensaver">
      <video autoplay loop muted>
        <source src="screensaver.mp4" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from "vue";
  
  defineProps({
    show: Boolean, // Accept 'show' state as a prop
  });
  
  const emit = defineEmits(["hide"]);
  
  const hideScreensaver = () => {
    emit("hide"); // Notify parent to hide the screensaver
  };
  </script>
  
  <style scoped>
  .screensaver {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: black;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
  }
  
  video {
    max-width: 100%;
    max-height: 100%;
  }
  </style>
  