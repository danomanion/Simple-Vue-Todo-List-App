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
import axios from 'axios'

export default {
  name: 'app',
  components: {
    TheHeader,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  }
}
</script>

<style>
</style>
