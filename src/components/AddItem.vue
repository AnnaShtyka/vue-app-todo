<template>
  <div>
    <b-container>
      <b-card-header header-tag="nav">
        <b-nav class="nav">
          <b-form @submit.prevent="onSubmit" class="form">
            <b-form-input
              type="text"
              v-model="title"
              placeholder="create item"
              class="input"
            ></b-form-input>
            <b-button type="submit" variant="success">create</b-button>
          </b-form>
        </b-nav>
      </b-card-header>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newItem = {
          id: Date.now(),
          title: this.title,
          completed: false,
        };
        this.$emit("add-item", newItem);
        this.title = "";
      }
    },
  },
};
</script>

<style scoped>
.nav {
  display: flex;
  justify-content: center;
}
.form {
  display: flex;
  width: 25rem;
}
.input {
  margin-right: 5px;
}
</style>
