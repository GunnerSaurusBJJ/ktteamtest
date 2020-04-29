<template>
  <div id="app">
    <h1>Todo app</h1>
    <addTodo @add-todo="TodoAdd" />
    <listTodo v-bind:todos="todos" v-on:remove-todo="removeTodo" v-if="todos.length" />
    <p v-else>Нет задач</p>
  </div>
</template>

<script>
import listTodo from "@/components/listTodo";
import addTodo from "@/components/addTodo";

export default {
  name: "App",
  components: { listTodo, addTodo },
  data() {
    return {
      todos: []
    };
  },

  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    TodoAdd(todo) {
      this.todos.push(todo);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  max-width: 300px;
  width: 100%;
  border: 2px solid;
  border-radius: 10px;
  background: #ccc;
  padding-left: 10px;
  padding-right: 10px;
}
</style>
