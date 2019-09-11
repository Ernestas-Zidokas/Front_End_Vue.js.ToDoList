<template>
  <div id="app">
    <div class="surface">
      <h1 class="headline">To Do List</h1>
      <BaseInputField v-model="newToDoText" labelText="You input"></BaseInputField>
      <BaseButton @click="onClick">Create</BaseButton>
    </div>
    <div>
      <ToDoList>
        <ToDoListItem
          v-for="(todo, index) in toDoList"
          :key="index"
          :todo="todo"
          @change="handleChange(index, $event)"
          @delete="handleDelete(index, $event)"
        />
      </ToDoList>
    </div>
  </div>
</template>

<script>
import BaseButton from "./components/BaseButton";
import BaseInputField from "./components/BaseInputField";
import ToDoList from "./components/ToDoList";
import ToDoListItem from "./components/ToDoListItem";

export default {
  name: "App",
  components: {
    BaseButton,
    BaseInputField,
    ToDoList,
    ToDoListItem
  },
  data() {
    return {
      toDoList: [],
      newToDoText: null
    };
  },
  methods: {
    onClick(event) {
      if (this.newToDoText) {
        this.toDoList = [
          ...this.toDoList,
          { text: this.newToDoText, done: false }
        ];
        this.newToDoText = null;
      }
    },
    handleChange(index, event) {
      this.toDoList = this.toDoList.map((item, i) => {
        if (i === index) {
          item.done = event.target.checked;
        }
        return item;
      });
      // this.toDoList[index].done = event.target.checked;
    },
    handleDelete(index, event) {
      this.toDoList = this.toDoList.filter((item, i) => i !== index);
    }
  }
};
</script>

<style lang="scss">
</style>
