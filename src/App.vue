<template>
  <div
    id="app"
    @mousemove="resetTimer"
    @keydown="resetTimer"
    @click="resetTimer"
    @touchstart="resetTimer"
    @scroll="resetTimer"
  >
    <!-- Screensaver -->
    <div v-if="isScreensaverActive" class="screensaver" @click="resetTimer">
      <video autoplay muted loop class="screensaver-video">
        <source src="screensaver2.mp4" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
      <!-- Tap to Know More CTA -->
      <div class="screensaver-cta">
        <p>Tap to know more</p>
      </div>
    </div>

    <!-- QR Code -->
    <div :class="['qr-code', { 'qr-code-hidden': hideQRCode }]" v-if="!isScreensaverActive">
      <img src="Qr.jpeg" alt="QR Code" />
    </div>

    <!-- Sections -->
    <component v-for="section in sections" :is="section.component" :key="section.name" />
  </div>
</template>




<script setup>
import { ref, onMounted, onUnmounted } from "vue";

// Import section components
import Section1 from "./components/Section1.vue";
import Section2 from "./components/Section2.vue";
import Section3 from "./components/Section3.vue";
import Section4 from "./components/Section4.vue";
import Section5 from "./components/Section5.vue";
import Section6 from "./components/Section6.vue";
import Section7 from "./components/Section7.vue";
import Section8 from "./components/Section8.vue";
import Section9 from "./components/Section9.vue";
import Section10 from "./components/Section10.vue";

// Sections definition
const sections = ref([
  { name: "Section1", component: Section1 },
  { name: "Section2", component: Section2 },
  { name: "Section3", component: Section3 },
  { name: "Section4", component: Section4 },
  { name: "Section5", component: Section5 },
  { name: "Section6", component: Section6 },
  { name: "Section7", component: Section7 },
  { name: "Section8", component: Section8 },
  { name: "Section9", component: Section9 },
  { name: "Section10", component: Section10 },
]);

// Reactive states
const hideQRCode = ref(false);
const isScreensaverActive = ref(false);

let timer; // Timer for inactivity

// Reset inactivity timer
const resetTimer = () => {
  isScreensaverActive.value = false; // Deactivate screensaver
  clearTimeout(timer); // Reset timer

  timer = setTimeout(() => {
    isScreensaverActive.value = true; // Activate screensaver after 10s of inactivity
  }, 20000); // 20 seconds

  if (event && event.type === "scroll") {
    const scrollPosition = event.target.scrollTop;
    const sectionHeight = window.innerHeight;
    const lastSectionTop = (sections.value.length - 2) * sectionHeight;

    hideQRCode.value = scrollPosition >= lastSectionTop;
  }
};

// Attach and clean up event listeners
onMounted(() => {
  resetTimer();
});

onUnmounted(() => {
  clearTimeout(timer);
});
</script>



<style>

html, body {
  margin: 0; /* Remove default margins */
  padding: 0; /* Remove default padding */
  height: 100vh; /* Ensure body spans full height */
  overflow: hidden; /* Prevent scrollbars caused by margin/padding issues */
  color: #4b4b4b;
  /* text-rendering: optimizeLegibility; */
}

#app {
  font-family: ppnm-Regular, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1d1b1b;
  /* text-rendering:optimizeLegibility; */

  /* Enable vertical scrolling with snapping */
  scroll-snap-type: y mandatory; /* Enable snap scrolling */
  overflow-y: scroll; /* Allow vertical scrolling */
  height: 100vh; /* Full viewport height */
  scrollbar-width: none; /* Hide scrollbar in Firefox */
  color: #4b4b4b;


}

.screensaver-cta {
  position: absolute;
  top: 20%; /* Center vertically */
  left: 50%; /* Center horizontally */
  transform: translate(-50%, -50%); /* Offset by 50% of its own dimensions */
  z-index: 10000;
  background-color: rgba(121, 23, 197, 0.784); /* Semi-transparent black background */
  padding: 20px 40px;
  border-radius: 25px;
  color: white;
  font-size: 1.5rem;
  font-weight: bold;
  text-align: center;
  box-shadow: 0 4px 10px rgba(112, 10, 208, 0.5);
  animation: pulse 2s infinite; /* Add a pulsing effect */
}

@keyframes pulse {
  0%, 100% {
    transform: translate(-50%, -50%) scale(1); /* Centered and default size */
  }
  50% {
    transform: translate(-50%, -50%) scale(1.1); /* Slightly enlarge */
  }
}



.section {
  scroll-snap-align: center; /* Snap each section to the top */
  height: 100vh; /* Full viewport height */
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 10px;
  margin: 5px;
  /* padding: 50px; */
}

/* Optional: Hide scrollbar for all browsers */
#app::-webkit-scrollbar {
  display: none;
}

.screensaver {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: black;
  z-index: 9999; /* Ensure it overlays everything */
  display: flex;
  justify-content: center;
  align-items: center;
}

.screensaver-video {
  width: 100%;
  height: 100%;
  object-fit: cover; /* Ensure video covers the entire screen */
}

.qr-code {
  position: fixed; /* Ensures it stays in the top right corner */
  top: 35px; /* Distance from the top of the viewport */
  right: 20px; /* Distance from the right of the viewport */
  z-index: 9999; /* Ensures it is above other elements */
  background: white; /* Background color for contrast */
  /* border: 2px solid #ccc; Optional: Add a border */
  padding: 0; /* Add spacing around the QR code */
  border-radius: 10px; /* Rounded corners */
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1); /* Optional: Shadow for depth */
  transition: transform 0.5s ease, opacity 0.5s ease; /*Smooth animation */
  opacity: 1; /*Fully visible */
  transform: translateY(0); 
  align-content: center;
  width: 100px;
  height: 100px;
}

.qr-code-hidden {
  opacity: 0; /* Fade out */
  transform: translateY(-300px); /* Move off-screen upward */
  z-index: 9999;
  pointer-events: none; /* Prevent interaction while hidden */
}

.qr-code img {
  width: 100px;
  height: auto;
  border-radius:10px;
}



</style>
