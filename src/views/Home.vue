<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <!-- 下级传来的del-todo事件被触发时，将会调用deleteTodo方法 -->
    <Todos v-bind:todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name : 'Home',
  components : {
    Todos,
    AddTodo,
  }, 
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      // filter out those id not equals the deleted item.
      // this.todos = this.todos.filter(x => x.id !== id);
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => {
        this.todos = this.todos.filter(x => x.id !== id);
      })
      .catch(err => console.log(err))
    },
    addTodo(newTodo) {
      // spread operator
      // this.todos = [...this.todos, newTodo];

      const {title, completed} = newTodo;
      axios.put('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = this.todos = [...this.todos, res.data])
      .catch(err => console.log(err))
    },
  }, 
  created() {
    // return a promise
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.todos = res.data)
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