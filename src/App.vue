<template>
  <div>
    <Header />
    <TodoInput v-on:add-todo="addtodo" />
    <div id="app">
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import Header from "./components/Header.vue";
import TodoInput from "./components/TodoInput.vue";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    TodoInput,
  },
  data() {
    return {
      todos: [
        { id: 1, name: "Jamal", completed: false },
        { id: 2, name: "Ahmad", completed: false },
        { id: 3, name: "Hasan", completed: false },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addtodo(newtodo) {
      this.todos = [...this.todos, newtodo];
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  justify-content: center;
}
</style>
