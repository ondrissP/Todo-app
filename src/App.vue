<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos :todos='todos' v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
//import axios from "axios";
export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
methods: {
  deleteTodo(id) {
//  axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
//    // eslint-disable-next-line no-unused-vars
//    .then(res => this.todos = this.todos.filter(todo =>
//    todo.id !== id))
//    .catch(err => console.log(err));
      this.todos = this.todos.filter(todo =>todo.id !== id);
  },
  addTodo(newTodo) {
//   const { title, completed } = newTodo;
//   axios.post('https://jsonplaceholder.typicode.com/todos', {
//     title,
//     completed
//   })
//     .then(res => this.todos = [...this.todos, res.data])
//     .catch(err => console.log(err));

     this.todos = [...this.todos, newTodo];
  }
},
//created() {
//  axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
//    .then(res => this.todos = res.data)
//    .catch(err => console.log(err));
//  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Indie+Flower&display=swap');

*{
  margin: 0 auto;
  padding: 0;
  font-family: 'Indie Flower', cursive;
}
body{
  background-color: #000000;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

[v-cloak]{
	display: none;
}
</style>
