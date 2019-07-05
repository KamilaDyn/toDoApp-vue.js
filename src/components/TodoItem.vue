<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <div class="item">
      <p>
        <input class="checkbox" type="checkbox" v-on:change="markComplete">
        {{todo.title}}
      </p>
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
      console.log(123);
    }
  }
};
</script>

<style scoped>
.todo-item {
  display: flex;
  flex-direction: column;
  margin: 10px auto;
  width: 80vw;
  background: lightblue;
  padding: 10px;
  border-bottom: 1px solid gray;
}
.is-complete {
  text-decoration: line-through;
}
.item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: baseline;
}

p {
  text-align: left;
  flex-wrap: wrap;
  padding: 10px;
  line-height: 1.5em
}
.checkbox {
  margin-right: 10px;
  border: 1px solid #1d3f77;
}
.del {
  background: red;
  border-radius: 50%;
  width: 20px;
  height: 20px;
  border: 1px solid red;
  color: white;
  line-height: 50%;
}
.del:hover {
  background-color: #1d3f77;
}
</style>