<template>
  <form @submit="onSubmit" class="form">
    <input type="text" v-model="text" name="text" placeholder="Add Task">
    <input type="text" v-model="day" name="day" placeholder="Add Day & Time">
    <div class="form--footer">
      <div class="reminder">
        <input class="switch-input" type="checkbox" v-model="reminder" name="reminder" id="reminder" />
        <label class="switch-label" for="reminder"></label>
      </div>
      <input type="submit" value="Save" class="btn btn-task">
    </div>
  </form>
</template>

<script>
  export default {
    name: "AddTask",
    data() {
      return {
        text: '',
        day: '',
        reminder: false,
      }
    },
    methods: {
      onSubmit(e) {
        e.preventDefault()

        if (!this.text || !this.day) {
          alert("Please provide completed information for a task!")
          return
        }

        const newTask = {
          text: this.text,
          day: this.day,
          reminder: this.reminder,
        }

        this.$emit('add-task', newTask)

        this.text = ''
        this.day = ''
        this.reminder = false
      }
    }
  }
</script>

<style scoped>
  .form {
    box-shadow: rgba(60, 64, 67, 0.1) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
    padding: 8px;
    border-radius: 5px;
    margin-bottom: 20px;
    transition: all ease 1s;
  }

  .form input[type='text'] {
    background-color: #f7f7f7;
    border: none;
    padding: 8px 12px;
    border-radius: 5px;
    font-size: 16px;
    font-family: 'Nunito';
    box-shadow: rgb(50 50 93 / 5%) 0px 3px 6px -12px inset, rgb(0 0 0 / 10%) 0px 6px 18px -18px inset;
    outline: none;
    margin-bottom: 8px;
    display: block;
    width: 100%;
    font-weight: 600;
  }

  .form--footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 8px 0;
  }

  .form--footer input[type='submit'] {
    margin: 0;
    box-shadow: none;
    padding: 6px 20px;
    font-size: 15px;
    font-weight: 300;
  }

  .reminder {
    position: relative;
    display: inline-block;
  }

  .switch-input {
    display: none;
  }

  .switch-label {
    display: block;
    width: 48px;
    height: 24px;
    text-indent: -150%;
    clip: rect(0 0 0 0);
    color: transparent;
    user-select: none;
  }

  .switch-label::before,
  .switch-label::after {
    content: "";
    display: block;
    position: absolute;
    cursor: pointer;
  }

  .switch-label::before {
    width: 100%;
    height: 100%;
    background-color: #dedede;
    border-radius: 9999em;
    -webkit-transition: background-color 0.25s ease;
    transition: background-color 0.25s ease;
  }

  .switch-label::after {
    top: 2px;
    left: 2px;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: #fff;
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.45);
    -webkit-transition: left 0.25s ease;
    transition: left 0.25s ease;
  }

  .switch-input:checked+.switch-label::before {
    background-color: #333333;
  }

  .switch-input:checked+.switch-label::after {
    left: 26px;
  }
</style>