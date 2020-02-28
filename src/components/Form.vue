<template>
  <div>
    <h1 class="text-center">{{title}}</h1>
    <form @submit.prevent="addTodo">
      <div class="form-group">
        <label for="newTodoApp">New Todo</label>
        <input
          v-model="newTodo"
          type="text"
          class="form-control"
          id="newTodoApp"
          aria-describedby="newTodoApp"
          placeholder="Create newTodo..."
        />
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
    <ul class="list-group mt-3" v-for="(todo, i) in todos" v-bind:key="todo.title">
      <li class="list-group-item">
        <button v-if="!todo.done" @click="markDone(todo)" class="btn btn-primary mr-3">Done</button>
        <button @click="deleteTodo(i)" class="btn btn-danger mr-3">Delete</button>

        <span :class="{isDone: todo.done}">{{todo.title}}</span>
      </li>
    </ul>
  </div>
</template>


<script>
export default {
  name: "Form",
  props: {
    title: String
  },
  data() {
    return {
      newTodo: "",
      todos: []
    };
  },
  watch: {
    todos: {
      handler() {
        localStorage.todos = JSON.stringify(this.todos);
      },
      deep: true
    }
  },
  mounted() {
    if (localStorage.todos) {
      this.todos = JSON.parse(localStorage.todos);
    }
  },
  methods: {
    addTodo() {
      this.todos.push({ title: this.newTodo, done: false });
      this.newTodo = "";
    },
    markDone(todo) {
      {
        todo.done === true ? (todo.done = false) : (todo.done = true);
      }
    },
    deleteTodo(i) {
      this.todos.splice(i, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.isDone {
  text-decoration: line-through;
  color: red;
}
</style>