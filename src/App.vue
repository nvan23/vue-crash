<template>
  <div class="container">
    <Header title="Task Tracker"></Header>
    <Tasks :tasks="tasks"></Tasks>
  </div>
</template>

<script>
  import Header from './components/Header'
  import Tasks from './components/Tasks'

  export default {
    name: 'App',
    components: {
      Header,
      Tasks,
    },
    data() {
      return {
        tasks: []
      }
    },
    created() {
      this.tasks = [
        {
          id: 1,
          text: 'Pick a random bug',
          day: 'March 1st at 2:30pm',
          reminder: true,
        },
        {
          id: 2,
          text: 'Pick a random pet',
          day: 'March 2st at 3:30pm',
          reminder: false,
        },
        {
          id: 3,
          text: 'Pick a random meal',
          day: 'March 3st at 4:30pm',
          reminder: true,
        }
      ]
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
    background: #202124;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
    box-shadow: 0px 4px 16px rgba(0, 0, 0, 0.3);
  }

  .btn:hover {
    opacity: 0.9;
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