<template>
  <div class="container" v-bind:class="{ 'is-completed': todo.completed }">
    <div class="div1">
      <input type="checkbox" v-on:change="MarkCompleted" />
      <h2>
        {{ todo.name }}
      </h2>
    </div>
    <p class="div1">{{ todo.id }}</p>
    <button class="div2" @click="$emit('del-todo', todo.id)" type="del">
      x
    </button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    MarkCompleted() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.container {
  background: #f0f0f0;
  flex-direction: row;
  display: flex;
}

.div1 {
  flex: 3;
}
.div2 {
  -ms-flex-item-align: end;
}

.is-completed {
  text-decoration: line-through;
}
</style>
