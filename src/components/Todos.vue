<template lang="html">
  <div>
    <template v-for="todo in todos">
      <TodoItem :todo="todo" @del-todo="$emit('del-todo', todo.id)"/>
    </template>
  </div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
  name: "Todos",
  props: ["todos"],
  components: {
    TodoItem
  }
}
</script>

<style lang="css" scoped>
</style>
