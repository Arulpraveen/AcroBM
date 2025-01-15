<template>
  <div class="image-container section">
    <!-- Title -->
    <h1 class="title">Available Colors</h1>

    <!-- Images and Descriptions -->
    <div class="images">
      <!-- White -->
      <div class="image-item">
        <img src="WHITE.png" alt="White" />
        <h2>White</h2>
        <p>A sleek and timeless color for a clean and modern look.</p>
      </div>

      <!-- Purple -->
      <div class="image-item">
        <img src="PURPLE.png" alt="Purple" />
        <h2>Purple</h2>
        <p>Express your unique style with a bold and vibrant purple.</p>
      </div>

      <!-- Red -->
      <div class="image-item">
        <img src="RED.png" alt="Red" />
        <h2>Red</h2>
        <p>A passionate and energetic color that stands out.</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ThreeImagesWithText",
};
</script>

<style scoped>
.image-container {
  text-align: center;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 136px;
  padding-bottom: 150px;
}

.title {
  font-size: 2rem;
  margin-bottom: 20px;
}

.images {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  gap: 20px;
  flex-wrap: wrap; /* Ensures responsiveness */
}

.image-item {
  width: 328px;
  text-align: center;
}

.image-item img {
  width: 100%;
  height: auto;
  border-radius: 10px;
  /* box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2); */
}

.image-item h2 {
  font-size: 1.5rem;
  margin: 10px 0 5px;
}

.image-item p {
  font-size: 1rem;
  color: #555;
}
</style>
