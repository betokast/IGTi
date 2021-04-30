<template>
  <h1>ToDo App</h1>
  <div>
    <div v-if="!editMode">
      <Button @click="newTodo">Novo</Button>
      <todo-list :todo="todos"></todo-list>
    </div>

    <div>
      <todo-item
        v-if="editMode"
        @cancel="cancel"
        @saveTodo="saveTodo"
      ></todo-item>
    </div>
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import TodoItem from "./components/TodoItem.vue";

export default {
  components: {
    TodoList,
    TodoItem,
  },
  data() {
    return {
      editMode: false,
      todos: [],
    };
  },
  methods: {
    newTodo() {
      this.editMode = true;
    },
    cancel() {
      this.editMode = false;
    },
    saveTodo(todo) {
      this.todos.push(todo);
      localStorage.setItem("todos", JSON.stringify(this.todos));
      this.editMode = false;
    },

    created() {
      const todos = localStorage.getItem("todos");
      if (todos) {
        this.todos = JSON.parse(todos);
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
