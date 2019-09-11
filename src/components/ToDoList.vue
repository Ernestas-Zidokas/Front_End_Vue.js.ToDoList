<template>
  <ul class="todo-list">
    <slot />
  </ul>
</template>

<script>
export default {
  name: "ToDoList"
};
</script>

<style lang="scss">
.todo-list {
}
</style>