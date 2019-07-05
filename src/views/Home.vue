<template>
  <div id="app" class="container">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          response => (this.todos = this.todos.filter(todo => todo.id !== id))
        )
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(response => (this.todos = [...this.todos, response.data]))
        .catch(err => console.log(err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then(response => (this.todos = response.data))
      .catch(err => console.log(err));
  }
};
</script>

<style>
.container {
  margin: 20px;
}
body {
  font-family: Arial, Georgia;
  line-height: 1.4px;
}
.btn {
  display: inline-block;
  border: none;
  background-color: purple;
  color: white;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: pink;
}
</style>
