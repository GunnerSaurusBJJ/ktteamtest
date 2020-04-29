<template>
  <div>
    <input type="text" v-model="title" @keyup.enter.prevent="onSubmit" />
    <button class="add" @click="onSubmit">Add todo</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: ""
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        };
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    }
  }
};
</script>

<style scoped>
.add {
  cursor: pointer;
  border: none;
  outline: none;
  background: rebeccapurple;
  color: #fff;
  text-transform: uppercase;
  border-radius: 5px;
  display: block;
  margin: 0 auto;
  padding: 10px 20px;
  margin-top: 10px;
}
input {
  width: 250px;
  height: 35px;
  border-radius: 5px;
  outline: none;
  border: none;
  padding-left: 10px;
  padding-right: 10px;
}
</style>