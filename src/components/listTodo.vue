<template>
  <div>
    <button class="sort" @click="sortTodo">Сортировать</button>
    <li v-for="todo in todos" :key="todo.id">
      <span v-bind:class="{done:todo.completed}">
        <input type="checkbox" @change="todo.completed = !todo.completed" />
        {{todo.title}}
      </span>
      <button class="delete" @click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
  </div>
</template>

<script>
export default {
  props: ["todos"],
  components: {},
  methods: {
    sortTodo() {
      this.todos.reverse();
    }
  }
};
</script>

<style scoped>
li {
  border: 1px solid #000;
  display: flex;
  justify-content: space-between;
  padding: 10px 30px;
  align-items: center;
  margin: 1rem auto;
}

.delete {
  background: red;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
  outline: none;
  border: none;
  cursor: pointer;
  padding: 7px 10px;
  margin-left: 10px;
}
input {
  margin-right: 1rem;
}
.done {
  text-decoration: line-through;
}

div {
  margin-bottom: 2rem;
  margin-top: 1rem;
}
.sort {
  cursor: pointer;
  border: none;
  outline: none;
  background: rgb(18, 18, 19);
  color: #fff;
  text-transform: uppercase;
  border-radius: 5px;
  display: block;
  margin: 0 auto;
  padding: 10px 20px;
}
</style>