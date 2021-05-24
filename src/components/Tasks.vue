<template>
  <transition-group name="list" tag="p">
    <div :key="task.id" v-for="task in tasks">
      <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)"
        :task="task">
      </Task>
    </div>
  </transition-group>
</template>

<script>
  import Task from './Task'
  export default {
    name: 'Tasks',
    props: {
      tasks: {
        type: Array,
      }
    },
    components: {
      Task
    },
    emits: ['delete-task', 'toggle-reminder'],
  }
</script>

<style>
  .list-enter-active,
  .list-leave-active {
    transition: all 0.5s;
  }

  .list-enter,
  .list-leave-to {
    opacity: 0;
    transform: translateY(10px);
  }
</style>