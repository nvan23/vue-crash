<template>
  <button class="btn" :style="{background: color}" @click="onClick()">
    {{text}}
  </button>
</template>

<script>
  export default {
    name: 'Button',
    props: {
      text: {
        type: String,
        default: "Button"
      },
      color: {
        type: String,
        default: "black"
      }
    },
    methods: {
      onClick() {

      }
    }
  }
</script>