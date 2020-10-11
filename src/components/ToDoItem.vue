<template>
  <div>
    <li>
      <span>
        <b-form-checkbox
          size="sm"
          v-on:change="todo.completed = !todo.completed"
        >
          {{ todo.title }}
        </b-form-checkbox>
      </span>
      <b-button
        size="sm"
        class="remove"
        v-on:click="$emit('remove-item', todo.id)"
        v-bind:class="{ done: todo.completed }"
        >delete</b-button
      >
    </li>
  </div>
</template>

<script>
export default {
  props: ["todo"],
};
</script>

<style scoped>
li {
  width: 30rem;
  border: 1px solid black;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem;
  margin-bottom: 1rem;
}

.remove {
  border: none;
  background: red;
  color: #fff;
}

.done {
  background: green;
}
</style>
