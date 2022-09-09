<template>
    <div>
        <div class="mainInfo">
            <h2>Todo Application</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis commodi dolorem nostrum modi magnam iste officiis magni asperiores quo laborum vero omnis, alias libero molestiae porro. Placeat a sint eius!</p>
            <router-link to="/" class="routerLink">Home</router-link>
        </div>
    <hr>
    <div class="search">
        <AddTodo 
        @add-todo="addTodo"
        />
        <select v-model="filter">
            <option value="all">All</option>
            <option value="completed">Completed</option>
            <option value="not-completed">Not Completed</option>
        </select>
    </div>
    <hr>
    <Loader v-if="loading" />
    <TodoList
      v-else-if="filteredTodos.length" 
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo" 
    />
    <p v-else>No todos!</p>
  </div>
  <hr>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import AddTodo from '@/components/AddTodo.vue'
import Loader from '@/components/Loader.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },

  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=7')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
            this.todos = json
            this.loading = false
        }, 1000)
      })
  },

  computed: {
      filteredTodos() {
          if(this.filter === 'all') {
              return this.todos
          }

          if(this.filter === 'completed') {
              return this.todos.filter(t => t.completed)
          }

          if(this.filter === 'not-completed') {
              return this.todos.filter(t => !t.completed)
          }
      }
  },

  components: {
      TodoList,
      AddTodo,
      Loader,
  },

  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },

    addTodo(todo) {
      this.todos.push(todo)
    }
  }
}
</script>

<style scoped>
.search {
    height: 100px;
    vertical-align: center;
    background-color: rgb(23, 189, 170);
}
</style>