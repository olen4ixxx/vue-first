<template>
  <div>
    <h2>TODO APP</h2>
    <router-link to="/">Home</router-link>
    <hr/>
    <AddTodo
        @add-todoElement="addTodoElement"
    />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <hr>
    <Loader v-if="loading"/>
    <TodoList
        v-else-if="filteredTodos.length"
        v-bind:todosElement="filteredTodos"
        @remove-todoElement="removeTodoElement"
    />
    <p v-else>No current todos</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
export default {
  name: 'App',
  data() {
    return {
      todos: [
        // {id: 1, title: 'To buy bread', completed: false},
        // {id: 2, title: 'To buy milk', completed: false},
        // {id: 3, title: 'To buy butter', completed: false}
      ],
      loading: true,
      filter: 'all'
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
        .then(response => response.json())
        .then(json => {
          setTimeout(() => {
            this.todos = json
            this.loading = false
          }, 500)
        })
  },
  components: {
    TodoList, AddTodo, Loader
  },
  methods: {
    removeTodoElement(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodoElement(todo) {
      this.todos.push(todo)
    }
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      } else if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      } else return this.todos
    }
  }
  // watch: {
  //   filter(value) {
  //     console.log(value)
  //   }
  // }
}
</script>

