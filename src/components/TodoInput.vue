<template>
  <form @submit="addtodo">
    <input type="text" name="name" v-model="name" placeholder="AddTodo" />
    <input type="submit" value="Submit" class="btn" />
  </form>
</template>

<script>
import { v4 as uuid } from "uuid";
export default {
  name: "TodoInput",
  data() {
    return {
      name: "",
    };
  },
  methods: {
    addtodo(e) {
      e.preventDefault();
      const newtodo = {
        id: uuid(),
        name: this.name,
        completed: false,
      };
      this.$emit("add-todo", newtodo);
      this.name = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>
