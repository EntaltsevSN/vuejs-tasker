<template>
  <li class="list-group-item d-flex justify-content-between align-items-center">
    <div class="custom-control custom-checkbox">
      <input type="checkbox" class="custom-control-input" v-bind:id="`task${todo.id}`" v-on:change="todo.completed = !todo.completed">
      <label class="custom-control-label" v-bind:for="`task${todo.id}`">
        <span class="ml-2" v-bind:class="{completed: todo.completed}">{{todo.title}}</span>
      </label>
      <span class="badge ml-3" 
        v-bind:class="`badge-${todo.status}`"
      >{{statusList.filter(item => item.value === todo.status)[0].title}}</span>
    </div>
    <a href="#" class="badge badge-danger badge-close" v-on:click.prevent="$emit('remove-todo', todo.id)">&times;</a>
  </li>
</template>

<script>
export default {
  props: ['statusList','index', 'todo']
}
</script>

<style lang="scss" scoped>
  .badge-close {
    font-size: 16px;
  }
  .completed {
    text-decoration: line-through;
    color: #999;
  }
  input {
    cursor: pointer;
  }
</style>