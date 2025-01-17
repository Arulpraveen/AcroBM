<template>
  <div class="video-container section">
    <!-- Video -->
    <video ref="videoPlayer" class="video-player" :src="videoSrc"></video>

    <!-- Controls -->
    <div class="controls">
      <div class="title">
        <div class="head">
          Three Adjustable Modes
        </div>
        <div class="content">
          Whether they’re just starting out or growing fast, this bike adapts to fit their needs. Adjust between three
          sizes to ensure your child’s riding experience is always safe, comfortable, and fun.
        </div>
      </div>
      <button :class="{ active: activeButton === 0 }" @click="setActive(0)">Small</button>
      <button :class="{ active: activeButton === 1 }" @click="setActive(1)">Medium</button>
      <button :class="{ active: activeButton === 2 }" @click="setActive(2)">Large</button>
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
    const activeButton = ref(0); // Default active button (Small)

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

    const setActive = (index) => {
      activeButton.value = index; // Set the active button
      seekTo(index); // Seek to the corresponding video timestamp
    };

    return {
      videoPlayer,
      videoSrc,
      activeButton,
      setActive,
      seekTo,
    };
  },
};
</script>

<style scoped>
.video-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 70px;
  padding: 40px
}

.video-player {
  width: 60%;
  max-width: 700px;
  border-radius: 10px;
  /* box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); */
}

.controls {
  display: flex;
  gap: 10px;
  flex-direction: column;
  padding: 30px;
  background-color: #1d1b1b;
  border-radius: 20px;
  align-items: center;
  max-width: 403px;
}

.controls .title {

  font-size: 24px;
  font-family: ppnm-Regular;
  color: white;
  text-align: left;
  /* margin-bottom: 10px; */
}

.controls .title .head{
  margin-bottom: 10px;
}

.controls .title .content {

font-size: 16px;
font-family: ppnm-Regular;
color: grey;
margin-bottom: 30px;
text-align: left;
}

button {
  height: 80px;
  width: 100%;
  padding: 10px 20px;
  background-color: #434343;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
  font-size: 24px;
}

button:hover {
  background-color: #ff5310;
}

button.active {
  background-color: #ff5310; /* Highlight active button */
  color: white;
  transform: scale(1.05); /* Slightly enlarge the active button */
}
</style>
