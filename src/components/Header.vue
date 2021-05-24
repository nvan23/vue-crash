<template>
  <header>
    <h1>{{title}}</h1>
    <Button v-show="onHomePage" :bgColor="!showAddTask ? '#1b1a1a' : '#ffffff'"
      :color="showAddTask ? '#1b1a1a' : '#ffffff'" @btn-click="$emit('toggle-add-task')"
      :icon="!showAddTask ? 'fas fa-plus' : 'fas fa-times'" :text="!showAddTask ? 'New' : 'Close'"></Button>
  </header>
</template>

<script>
  import Button from './Button'
  export default {
    name: 'Header',
    props: {
      title: {
        type: String,
        default: "Hello nvan23",
      },
      showAddTask: {
        type: Boolean,
      }
    },
    components: {
      Button
    },
    computed: {
      onHomePage() {
        if (this.$route.path === '/') {
          return true
        }
        return false
      }
    }
  }
</script>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>