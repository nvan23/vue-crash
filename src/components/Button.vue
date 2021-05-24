<template>
  <button class="btn" :style="{background: bgColor, color: color}" @click="onClick()">
    <i :class="icon"></i> {{text}}
  </button>
</template>

<script>
  export default {
    name: 'Button',
    props: {
      text: {
        type: String,
      },
      color: {
        type: String,
      },
      bgColor: {
        type: String,
      },
      icon: {
        type: String,
      }
    },
    methods: {
      onClick() {
        this.$emit('btn-click')
      }
    }
  }
</script>

<style scoped>
  button i {
    margin-right: 6px;
  }
</style>