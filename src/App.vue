<template>
  <div id="app">
    <nav>
      <h2 class="text-center">Simple todo</h2>
    </nav>
    <div class="container">
      <AddTodo v-on:add-todo="addTodo"/>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import Todos from "./components/Todos.vue";
import todos from "@/data/todos";

import axios from "axios";

export default {
  name: "app",
  components: {
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: todos
    };
  },
  methods: {
    addTodo(newTodo) {
      //this.todos.push(newTodo);
      axios
      .post("http://localhost:5500/todos",newTodo)
      .then(results => {
        this.todos=[...this.todos,results.data];
//        console.log();
      })
      .catch(err => console.error(err));
    },
    deleteTodo(id) {
      //this.todos = this.todos.filter(a => a.id !== id);
      axios
      .delete(`http://localhost:5500/todos/${id}`)
      .then(results => {
        this.todos = this.todos.filter(a => a._id !== id);
      //console.log(id);
      })
      .catch(err => console.error(err));
    }
  },
  created() {
    axios
      .get("http://localhost:5500/todos")
      .then(results => {
        this.todos=results.data;
//        console.log();
      })
      .catch(err => console.error(err));
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
nav {
  background-color: #df1a47;
  padding: 20px 0;
}
nav h2 {
  color: #fff;
  text-transform: uppercase;
  font-weight: 600;
}
.container {
  padding-top: 50px;
}
</style>
