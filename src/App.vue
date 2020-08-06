<template>
  <div id="app" >
    <Header />
    <div class="container">
      <AddTodo v-on:add-todo="addTodo" />
      <Todos v-bind:todos="todos" v-on:delete-item="deleteItem" />
    </div>
  </div>
</template>

<script>
import Header from './components/layout/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Todo One',
          completed: false
        },
        {
          id: 2,
          title: 'Todo Two',
          completed: true
        },
        {
          id: 3,
          title: 'Todo Three',
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteItem(id) {
      this.todos = this.todos.filter(item => item.id !== id)
    },
    addTodo(newItem) {
      this.todos = [...this.todos, newItem]
    }
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
