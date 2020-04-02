<template>
  <ul class="list-group mt-4">
    <TodoItem 
      v-bind:statusList="statusList"
      v-for="(todo, index) of todos"
      :key="index" :todo="todo"
      @remove-todo="removeTodo" />
  </ul>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
  components: {
    TodoItem
  },
  props: ['statusList', 'todos'],
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id);
    } 
  }
}
</script>