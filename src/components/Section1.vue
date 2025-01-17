<template>
  <div class="section section1">

    <video autoplay muted loop preload="none" class="background-video">
      <source src="HeroPage.mp4" type="video/mp4" />
      Your browser does not support the video tag.
    </video>
    <div class="overlay-text">
      <img src="vida.svg" alt="VIDA Logo" class="vida-logo" />
      <h2>ACRO</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "Section1",
};
</script>

<style scoped>
@import '../assets/fonts/stylesheet.css';

.box{

  padding: 5px;

}

.section1 {
  position: relative; /* Needed for absolute positioning inside */
  height: 100vh; /* Ensures it takes full viewport height */
  overflow: hidden; /* Ensures content doesn't overflow */
  display: flex;
  align-items: center;
  justify-content: center;
  /* padding: 100px; */
}

.overlay-text h1{

  font-family: ppnm-Bold, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  font-size: 80px;
  margin-bottom: 10px

}

.overlay-text h2{

  font-family: ppnm-SemiBoldItalic, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  

  font-size: 32px;
  margin-top: 0px
}

.vida-logo {
  width: 285px; /* Adjust the width of the logo */
  height: auto; /* Maintain aspect ratio */
}

.background-video {
  will-change: transform;
  transform: translateZ(0);
  position: absolute; /* Ensures the video stays in the viewport */
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1; /* Sends the video behind the content */
}

.overlay-text {
  position: relative; /* Allows the text to be on top of the video */
  color: white;
  text-align: center;
  z-index: 1; /* Stays above the video */
  font-size: 2rem;
  /* text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.7); */
}
</style>
