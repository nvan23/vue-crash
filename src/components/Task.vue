<template>
  <transition name="fade">
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
      <div class="task--left">
        <h3 class="title">
          {{ task.text }}
        </h3>
        <p class="day">{{ task.day }}</p>
      </div>
      <div class="task--right">
        <i @click="$emit('delete-task', task.id)" class="fas fa-trash"></i>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'Task',
    props: {
      task: {
        type: Object,
      }
    },
  }
</script>

<style scoped>
  .fas {
    color: #111111;
    opacity: 0.8;
  }

  .task {
    margin: 10px 0;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 5px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;
    border: 1px solid #ffffff;
    transition: transform .1s;
  }

  .task:hover {
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
    transform: scale(1.01);
  }

  .task.reminder {
    border: 1px solid #838383;
  }

  .task--right i {
    font-size: 18px;
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
    transition: all ease 0.12s;
  }

  .task--right i:hover {
    transform: scale(1.2);
  }

  .day {
    color: #757575;
  }

  .title {
    color: #202020;
  }
</style>