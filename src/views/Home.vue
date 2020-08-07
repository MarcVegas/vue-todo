<template>
  <div id="app" >
    <div class="container">
      <AddTodo v-on:add-todo="addTodo" />
      <Todos v-bind:todos="todos" v-on:delete-item="deleteItem" />
    </div>
  </div>
</template>

<script>
import Todos from '../components/Todos'
import AddTodo from '../components/AddTodo'

import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteItem(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(this.todos = this.todos.filter(item => item.id !== id))
      .catch(err => console.log(err))
    },
    addTodo(newItem) {
      const {title, completed} = newItem

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      }).then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err))
      
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.todos = res.data)
    .catch(err => console.log(err))
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
  font-family: 'Montserrat', sans-serif;
  background-color: rgb(241, 238, 234);
}

.container {
  margin: 0 30%;
}
</style>

