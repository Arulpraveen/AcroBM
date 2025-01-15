<template>
  <div id="app" @mousemove="resetTimer" @keydown="resetTimer" @click="resetTimer" @touchstart="resetTimer" @scroll="handleScroll">

    <div
      v-if="!hideQRCode"
      class="qr-code"
    >
      <img src="QR.png" alt="QR Code" />
    </div>

    <!-- Sections -->
    <component v-for="section in sections" :is="section.component" :key="section.name" />

    <!-- <interactive-video class="section"></interactive-video> -->

  </div>
</template>


<script setup>
import { ref } from "vue";

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
// import InteractiveVideo from "./components/InteractiveVideo.vue";

// Define sections dynamically
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

const hideQRCode = ref(false);

// Handle scroll event
const handleScroll = (event) => {
  const scrollPosition = event.target.scrollTop;
  const sectionHeight = window.innerHeight; // Assuming each section is full height
  const totalSections = sections.value.length;
  const lastSectionTop = (totalSections - 2) * sectionHeight;

  // Debugging log to verify scroll position
  console.log("Scroll Position:", scrollPosition);
  console.log("Last Position:", lastSectionTop);
  console.log("hideQRCode:", hideQRCode.value);
  

  // Hide QR code when the last section is in view
  hideQRCode.value = scrollPosition >= lastSectionTop;
};

</script>



<style>
/* @import '/assets/fonts/stylesheet.css'; */

html, body {
  margin: 0; /* Remove default margins */
  padding: 0; /* Remove default padding */
  height: 100vh; /* Ensure body spans full height */
  overflow: hidden; /* Prevent scrollbars caused by margin/padding issues */
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
}

.section {
  scroll-snap-align: center; /* Snap each section to the top */
  height: 100vh; /* Full viewport height */
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Optional: Hide scrollbar for all browsers */
#app::-webkit-scrollbar {
  display: none;
}

.qr-code {
  position: fixed; /* Ensures it stays in the top right corner */
  top: 20px; /* Distance from the top of the viewport */
  right: 20px; /* Distance from the right of the viewport */
  z-index: 9999; /* Ensures it is above other elements */
  background: white; /* Background color for contrast */
  /* border: 2px solid #ccc; Optional: Add a border */
  padding: 0; /* Add spacing around the QR code */
  border-radius: 10px; /* Rounded corners */
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1); /* Optional: Shadow for depth */
  transition: transform 0.2s ease, opacity 0.5s ease; /*Smooth animation */
  opacity: 1; /*Fully visible */
  transform: translateY(0); 
  align-content: center;
  width: 100px;
  height: 100px;
}

.qr-code-hidden {
  opacity: 0; /* Fade out */
  transform: translateY(-50px); /* Move off-screen upward */
  z-index: 9999;
  pointer-events: none; /* Prevent interaction while hidden */
}

.qr-code img {
  width: 100px;
  height: auto;
}



</style>
