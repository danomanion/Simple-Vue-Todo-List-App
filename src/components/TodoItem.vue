<template lang="html">
  <div class="collection-item row" @click="completedToggle()">
    <a class="col s1">
      <i class="material-icons">{{ checkBoxToggle() }}</i>
    </a>
    <div class="col s10" :class="{ 'is-completed' : todo.completed }">
      <span class="title">{{ todo.title }}</span>
    </div>
    <div class="actions col s1">
      <a class="secondary-content" @click="$emit('del-todo', todo.id)">
        <i class="material-icons">delete_forever</i>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ['todo'],
  methods: {
    completedToggle: function() {
      this.todo.completed = !this.todo.completed;
    },
    checkBoxToggle: function() {
      if (this.todo.completed == true) {
        return 'check_box'
      } else {
        return 'check_box_outline_blank'
      }
    }
  }
}
</script>

<style lang="css" scoped>
/* .title {
  padding-left: px;
} */
.collection-item {
  cursor: pointer;
}
.is-completed {
  background-color: red;
}
</style>
