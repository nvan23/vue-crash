<template>
  <footer>
    <div class="donate">
      <router-link to="/about" v-show="onAboutPage">👋 Give me a coffee ☕️ </router-link>
    </div>
  </footer>
</template>

<script>
  export default {
    name: 'Footer',
    computed: {
      onAboutPage() {
        if (this.$route.path === '/about') {
          return false
        }
        return true
      }
    }
  }
</script>

<style scoped>
  footer {
    margin-top: 30px;
    text-align: center;
  }

  a {
    text-decoration: none;
    color: #000000;
    font-family: 'Nunito', sans-serif;
    font-weight: 800;
    font-size: 18px;
  }

  .donate {
    transition: transform .1s;
  }

  .donate:hover {
    transform: scale(1.05);
  }
</style>