<template>
  <div class="container">
    <form @submit="addTodo">
      <input class="input" type="text" v-model="title" name="title" placeholder="add to do" />
      <input class="btn" type="submit" value="submit" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();

      const newTodo = {
        title: this.title,
        completed: false
      };
      //send to parents
      this.$emit("add-todo", newTodo);
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  flex-wrap: wrap;
}
form {
  display: flex;
  flex-wrap: wrap;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
  background: #1d3f77;
  font-weight: bold;
  letter-spacing: 3px;
}
</style>
