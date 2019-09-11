<template>
  <div id="app">
    <TheHeader />
    <Todos :todos="todos" @del-todo="deleteTodo"/>
    <hr>
    <AddTodo @add-todo="addTodo" />
  </div>
</template>

<script>
import TheHeader from './components/layout/TheHeader'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'

export default {
  name: 'app',
  components: {
    TheHeader,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {id: 1, title: "clean x y z", completed: false },
        {id: 2, title: "clean MORE x y z a b c", completed: true },
        {id: 3, title: "clean EVENT MORE x y z a b c d e f g h j k l m n o p q r s t u v w", completed: false },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  }
}
</script>

<style>
</style>
