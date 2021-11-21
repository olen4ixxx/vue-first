<template>
  <div>
    <ul>
      <TodoItem
          v-for="(t, i) of todosElement" :key="t"
          v-bind:todoElement="t"
          v-bind:index="i"
          v-on:remove-todoElement="removeTodoElement"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
  props: ['todosElement'],
  components: {
    TodoItem
  },
  methods: {
    removeTodoElement(id) {
      this.$emit('remove-todoElement', id)
    }
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>