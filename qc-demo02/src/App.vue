<template>
  <div id="app">
    <div class="todo-container">
      <div class="todo-wrap">
        <todo-header :addTodo="addTodo"/>
        <todo-list :todos="todos"/>
        <todo-footer :todos="todos" :selectAll="selectAll" :deleteCompleteTodos="deleteCompleteTodos"/>
      </div>
    </div>
  </div>
</template>

<script>

import TodoFooter from './components/TodoFooter'
import TodoHeader from './components/TodoHeader'
import TodoList from './components/TodoList'

export default {
  data() {
    return {
      todos: [
        {content: '真好学1', check: true},
        {content: '真好学2', check: false},
        {content: '真好学3', check: true},
        {content: '真好学4', check: true}
      ]
    }
  },
  methods: {
    addTodo(todo) {
      this.todos.unshift(todo)
    },
    selectAll(isSelectAll) {
      this.todos.forEach(todo => {
        todo.check = isSelectAll
      })
    },
    deleteCompleteTodos() {
      this.todos = this.todos.filter(todo => !todo.check)
    }
  },
  components: {
    TodoHeader,
    TodoList,
    TodoFooter
  }
}
</script>

<style>
.todo-container {
  width: 600px;
  margin: 0 auto;
}

.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
