<!-- Section5.vue -->
<template>
    <div class="section section5">
      <video autoplay muted loop class="background-video">
      <source src="adjustability.mp4" type="video/mp4" />
      Your browser does not support the video tag.
    </video>
    <div class="glassmorphic-box">
      <p>
        This bike adapts in three sizes to ensure a perfect fit at every stage of your child’s growth. A bike that truly grows with them!
      </p>
    </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "Section5",
  };
  </script>
  
  <style scoped>

p{

margin-block-start: 0;
margin-block-end: 0;
}


  .section5 {
  
  position: relative;
  height: 100vh;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;

  }

  .background-video {
    will-change: transform;
    transform: translateZ(0);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.glassmorphic-box {
  position: absolute;
  bottom: 40px; /* Adjust to position above the bottom */
  left: 40px; /* Adjust to position from the left */
  padding: 20px;
  width: 300px; /* Adjust the size of the box */
  background: rgba(0, 0, 0, 0.4); /* Transparent white */
  border-radius: 15px; /* Rounded corners */
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1); /* Subtle shadow */
  backdrop-filter: blur(20px); /* Blur effect */
  -webkit-backdrop-filter: blur(10px); /* Blur effect for Safari */
  border: 1px solid rgba(255, 255, 255, 0.3); /* Transparent border */
  color: #ffffff; /* Text color */
  font-size: 1rem; /* Adjust font size */
  line-height: 1.5;
  text-align: left;
  padding: 32px;
}
  </style>
  