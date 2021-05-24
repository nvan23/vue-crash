<template>
  <div class="container">
    <Header title="Task Tracker" @toggle-add-task="toggleAddTask" :showAddTask="showAddTask"></Header>
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer></Footer>
  </div>
</template>

<script>
  import Header from './components/Header'
  import Footer from './components/Footer'

  export default {
    name: 'App',
    components: {
      Header,
      Footer,
    },
    data() {

      console.log(this.$route)
      return {
        showAddTask: false,
      }
    },
    methods: {
      toggleAddTask() {
        this.showAddTask = !this.showAddTask
      },
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200;0,300;0,400;0,600;0,700;0,800;0,900;1,200;1,300;1,400;1,600;1,700;1,800;1,900&display=swap');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: 'Nunito', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100vw;
    height: 100vh;
    color: #111111;
  }

  .container {
    margin: auto;
    min-width: 450px;
    overflow: auto;
    padding: 30px;
    border-radius: 5px;
    box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.2);
  }

  .btn {
    display: inline-block;
    background: #1b1a1a;
    color: #fff;
    border: none;
    padding: 8px 14px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: 'Nunito', sans-serif;
    font-weight: 900 !important;
    box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.3);
    border: 1px solid #1b1a1a;
  }

  .btn:hover {
    background: #ffffff !important;
    color: #1b1a1a !important;
    transition: background 500ms ease;
    font-size: 15px;
    font-family: 'Nunito', sans-serif;
    font-weight: 1000 !important;
  }

  .btn:focus {
    outline: none;
  }

  .btn:active {
    transform: scale(0.98);
  }

  .btn-block {
    display: block;
    width: 100%;
  }
</style>