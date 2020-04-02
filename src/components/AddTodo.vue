<template>
  <form class="form-inline mt-4" @submit.prevent="submitForm">
    <input type="text" class="form-control" id="todo" placeholder="Task name" v-model="title">
    <select class="custom-select ml-3" v-model="status">
      <option v-for="(status, index) of statusList" :key="index" v-bind:value="status.value">{{status.title}}</option>
    </select>
    <button type="submit" class="btn btn-primary ml-3">Add task</button>
  </form>
</template>

<script>
export default {
  props: ['todos', 'statusList'],
  data() {
    return {
      title: '',
      status: 'secondary'
    }
  },
  methods: {
    submitForm() {
      (this.title.trim()) && this.$emit('add-todo', {
        id: this.todos.length + 1,
        title: this.title,
        status: this.status,
        completed: false
      })
      this.title = ''
      this.status = 'secondary'

    }
  }
}
</script>

<style lang="scss" scoped>
  input {
    flex-grow: 1;
  }
</style>