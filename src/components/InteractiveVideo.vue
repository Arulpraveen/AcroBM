<template>
    <div class="video-container">
      <!-- Video -->
      <video ref="videoPlayer" class="video-player" :src="videoSrc" controls></video>
  
      <!-- Controls -->
      <div class="controls">
        <button @click="seekTo(0)">Go to 0 sec</button>
        <button @click="seekTo(1)">Go to 10 sec</button>
        <button @click="seekTo(2)">Go to 15 sec</button>
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from "vue";
  
  export default {
    name: "InteractiveVideo",
    setup() {
      const videoPlayer = ref(null);
      const videoSrc = "Acro.mp4"; // Replace with your video file path
  
      const seekTo = (time) => {
        const video = videoPlayer.value;
        if (video) {
          // Smooth transition to the target time
          const step = (time - video.currentTime) / 30; // Adjust for smoothness
          let frame = 0;
          const interval = setInterval(() => {
            video.currentTime += step; // Incrementally change currentTime
            frame++;
            if (frame >= 30 || Math.abs(video.currentTime - time) < 0.1) {
              clearInterval(interval);
              video.currentTime = time; // Ensure exact timestamp
            }
          }, 33); // Approx. 30 frames per second
        }
      };
  
      return {
        videoPlayer,
        videoSrc,
        seekTo,
      };
    },
  };
  </script>
  
  <style scoped>
  .video-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
  }
  
  .video-player {
    width: 100%;
    max-width: 800px;
    border-radius: 10px;
    /* box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); */
  }
  
  .controls {
    display: flex;
    gap: 10px;
  }
  
  button {
    padding: 10px 20px;
    background-color: #1d1b1b;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #333;
  }
  </style>
  