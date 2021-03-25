<template>
  <div>
    <h3>Todos</h3>
    <div class="todos">
      <div
        @dblclick="ondblclick(todo)"
        v-for="todo in allTodos"
        :key="todo.id"
        class="todo"
        v-bind:class="{ 'is-complete': todo.completed }"
      >
        {{ todo.title }}
        <button @click="deleteTodo(todo.id)" class="remove">remove</button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "Toddos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    ondblclick(todo) {
      const updTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed,
      };
      this.updateTodo(updTodo);
    },
  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  },
};
</script>

<style scoped>
.todos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
.todo {
  border: 1px solid #ccc;
  background: #41b883;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}
.remove {
  position: absolute;
  bottom: 10px;
  right: 10px;
  color: #fff;
  background: rgb(113, 188, 201);
  cursor: pointer;
}

.is-complete {
  background: cadetblue;
  color: #fff;
}
</style>
