<template lang="html">
  <div class="todo-item">
    {{ todo.id }}
    <h3
      v-text="todo.title"
      :class="{ 'is-completed' : todo.completed }"
      @click="completedToggle()"
    />
    <button @click="$emit('del-todo', todo.id)" class="delete-btn">🗑️ Delete</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['todo'],
  methods: {
    completedToggle: function() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style lang="css" scoped>
  h3 {
    background-color: gold;
    cursor: pointer;
    margin-bottom: 3px;
    padding: 10px 20px;
  }

  .is-completed {
    text-decoration: line-through;
  }

  h3::before {
    content: "☐";
    padding-right: 20px;
  }

  h3.is-completed::before {
    content: "☑️";
  }

  .delete-btn {
    background-color: pink;
    padding: 5px 8px;
  }
</style>
