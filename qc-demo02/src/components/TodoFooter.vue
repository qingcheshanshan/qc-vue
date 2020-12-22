<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="checkAll"/>
    </label>
    <span>
          <span>已完成{{ checkSize }}</span> / 全部{{ todos.length }}
        </span>
    <button class="btn btn-danger" v-show="checkSize" @click="clearCheck">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  computed: {
    checkSize() {
      return this.todos.reduce((preTotal, todo) => preTotal + (todo.check ? 1 : 0), 0
      )
    },
    checkAll: {
      get() {
        return this.checkSize === this.todos.length && this.todos.length > 0
      },
      set(value) {
        this.selectAll(value)
      }
    }
  },
  methods: {
    clearCheck() {
      this.deleteCompleteTodos()
    }
  },
  props: {
    todos: Array,
    selectAll: Function,
    deleteCompleteTodos: Function
  }

}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}

</style>
