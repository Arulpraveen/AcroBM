<!-- Section10.vue -->
<template>
    <div class="section section10">
      <div class="content">
        <h2>
          Ready to bring this adventure home?
        </h2>
        <h1>Scan the QR Code</h1>
      </div>
      <div class="qr">
        <img src="QR.png" alt="QR code" />
      </div>

    </div>
  </template>
  
  <script>
  export default {
    name: "Section1",
  };
  </script>
  
  <style scoped>
  .section10 {
    /* Section-specific styles */
    background: #f0f0f0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 116px;
    background-color: #1e1e1e;
  }

  .section10{
    padding-left: 165px;
    padding-right: 165px;
  }

  .content{
    text-align: left;
    color: #f3f3f3;
  }

  .content h2{

    font-size: 20px;
    font-family: ppnm-Thin;
    padding-bottom: 0;
    margin: 0;
    color: #c9c9c9;
  }

  .content h1{
    margin: 0;
  }
  </style>
  