<template>
  <div id="app">
    <AddItem @add-item="addItem" />
    <TodoList v-bind:todos="todos" @remove-item="removeItem" />
  </div>
</template>

<script>
import TodoList from "./components/TodoList";
import AddItem from "./components/AddItem";
export default {
  name: "App",
  components: { TodoList, AddItem },
  data() {
    return {
      todos: [],
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then((response) => response.json)
      .then((json) => {
        this.todos = json;
      });
  },
  methods: {
    removeItem(id) {
      this.todos = this.todos.filter((elem) => elem.id !== id);
    },
    addItem(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style></style>
