<template>
  <li :class="['todo-list-item', {'todo-list-item-checked': todo.done}]">
    <input type="checkbox" :checked="todo.done" @change="handleChange" />
    {{todo.text}}
    <button @click="handleDelete">x</button>
  </li>
</template>

<script>
export default {
  name: "ToDoListItem",
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    handleChange(event) {
      this.$emit("change", event);
    },
    handleDelete(event) {
      this.$emit("delete", event);
    }
  }
};
</script>

<style lang="scss">
.todo-list-item {
  display: inline-block;
  &-checked {
    background: green;
  }
}
</style>