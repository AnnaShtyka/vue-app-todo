<template>
  <div>
    <b-container>
      <b-card title="Card Title" no-body>
        <b-card-body class="text-center">
          <b-card-text>
            <h2>To do List</h2>
            <ul class="list">
              <ToDoItem
                v-for="todo in todos"
                :key="todo.id"
                v-bind:todo="todo"
                v-on:remove-item="removeItem"
              />
            </ul>
          </b-card-text>
        </b-card-body>
      </b-card>
    </b-container>
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem";

export default {
  name: "TodoList",
  props: ["todos"],
  components: { ToDoItem },
  methods: {
    removeItem(id) {
      this.$emit("remove-item", id);
    },
  },
};
</script>

<style>
.list {
  display: flex;
  flex-direction: column;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>

>
