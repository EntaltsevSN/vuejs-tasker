<template>
  <div id="app">
    <Navbar />
    <div class="container">
      <About />
      <h2>Task manager</h2>
      <AddTodo v-bind:statusList="statusList" v-bind:todos="todos" @add-todo="addTodo" />
      <TodoList v-bind:statusList="statusList" v-bind:todos="todos" @remove-todo="removeTodo" />
    </div>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar';
import About from '@/components/About';
import AddTodo from '@/components/AddTodo';
import TodoList from '@/components/TodoList';

export default {
  name: 'App',
  components: {
    Navbar,
    About,
    AddTodo,
    TodoList
  },
  data() {
    return {
      todos: [
        {
          id: 0,
          title: 'Проверить работу приложения',
          status: 'secondary',
          completed: false  
        }
      ],
      statusList: [
        {
          value: 'secondary',
          title: 'Optional'
        },
        {
          value: 'success',
          title: 'Helpful'
        },
        {
          value: 'warning',
          title: 'Recommended'
        },
        {
          value: 'danger',
          title: 'Important'
        }
      ]
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(todo) {
      this.todos = [ ...this.todos, todo];
    }
  }
}
</script>

<!-- <style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->