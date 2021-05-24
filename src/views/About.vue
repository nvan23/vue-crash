<template>
  <div class="about">
    <h3>hello guy, why did you come here?</h3>
    <div class="back-home">
      <router-link to="/"> 👉 Back to Tasks Tracker </router-link>
    </div>
  </div>
</template>

<style scoped>
  h3 {
    margin: 20px;
  }

  a {
    text-decoration: none;
    color: #000000;
    font-family: 'Nunito', sans-serif;
    font-weight: 800;
    font-size: 18px;
  }

  .back-home {
    text-align: center;
  }

  .back-home:hover {
    transform: scale(1.05);
  }
</style>