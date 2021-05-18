<template>
  <div :class="[task.reminder ? 'reminder' : '', 'task']">
    <div class="task--left">
      <h3>
        {{ task.text }}
      </h3>
      <p>{{ task.day }}</p>
    </div>
    <div class="task--right">
      <i class="fas fa-trash"></i>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Task',
    props: {
      task: {
        type: Object,
      }
    }
  }
</script>

<style scoped>
  .fas {
    color: #202124;
  }

  .task {
    margin: 10px 0;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 5px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.08);
    display: flex;
    flex-wrap: nowrap;
    align-items: center;
    justify-content: space-between;
  }

  .task.reminder {
    border: 1px solid #202124;
  }

  .task--right i {
    box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
  }
</style>