<template>
  <div id="app">
   <CreateTodo @create-todo="CreateTodo" /> 
    <Todos :todos="todos" @dele-todo = "deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todos';
import CreateTodo from '../components/CreateTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    CreateTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods:{
     deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err));
    },  CreateTodo(todo) {
      const  title =todo.title;
        const  completed  = todo.completed;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data]) //[...this.todos, res.data]) is like push new item to array
        .catch(err => console.log(err));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => { this.todos = res.data})
      .catch(err => console.log(err));
  }
}

</script>

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
