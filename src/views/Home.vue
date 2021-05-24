<template>
  <div class="home">
    <AddTask v-show="showAddTask" @add-task="addTask"></AddTask>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"></Tasks>
  </div>
</template>

<script>
  import axios from 'axios'

  import Tasks from '../components/Tasks'
  import AddTask from '../components/AddTask'

  export default {
    name: "Home",
    props: {
      showAddTask: {
        type: Boolean,
      }
    },
    components: {
      Tasks,
      AddTask,
    },
    data() {
      return {
        tasks: [],
      }
    },
    methods: {
      async fetchTasks() {
        const res = await axios.get(`api/tasks`)
        return res.data
      },
      async fetchTask(id) {
        const res = await axios.get(`api/tasks/${id}`)
        return res.data
      },
      async addTask(task) {
        const res = await axios.post(`api/tasks`, task)
        this.tasks = [...this.tasks, res.data]
      },
      async deleteTask(id) {
        if (confirm('Are you sure?')) {
          const res = await axios.delete(`api/tasks/${id}`)
          res.status === 200
            ? this.tasks = this.tasks.filter(t => t.id !== id)
            : alert('Cannot to delete task now!')
        }
      },
      toggleReminder(id) {
        this.tasks.forEach(
          async (t, i) => {
            if (t.id === id) {
              const res = await axios.patch(`api/tasks/${id}`, { reminder: !t.reminder })
              t = { t, ...res.data }
              this.tasks.splice(i, 1, t)
              return this.tasks
            }
          })
      }
    },
    async created() {
      this.tasks = await this.fetchTasks()
    }
  }
</script>