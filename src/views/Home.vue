<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import Header from '../components/layouts/Header';
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id)) 
        .catch(err => console.log(err));
      
    },
    addTodo(newTodo) {
      const {title, completed } = newTodo; 
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, newTodo]) //gives back todo but with the id
        .catch(err => console.log(err));
      
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

/* Global to the application */
<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn { 
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
