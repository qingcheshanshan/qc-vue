<template>
  <ul class="todo-main">
    <TodoItem v-for="(todo,index) in todos" :deleteTodo="deleteTodo" :key="index" :index="index" :todo="todo"/>
  </ul>
</template>

<script>
import TodoItem from './TodoItem'

export default {
  props: ['todos', 'deleteTodo'], // 会成为当前组件对象的属性, 可以在模板中直接访问, 也可以通过this来访问

  components: {
    TodoItem
  }
}
</script>

<style scoped>

/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
