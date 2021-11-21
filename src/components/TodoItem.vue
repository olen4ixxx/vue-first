<template>
  <li>
    <div>
      <span v-bind:class="{done: todoElement.completed}">
        <input type="checkbox" v-on:change="todoElement.completed = !todoElement.completed">
        <strong>{{ index + 1 }}</strong>
        {{ todoElement.title | uppercase}}
      </span>
      <button class="rm" v-on:click="$emit('remove-todoElement', todoElement.id)">&times;</button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    todoElement: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: .5rem 2rem;
  margin-bottom: 1rem;
}

.rm {
  background: red;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
}

input {
  margin-right: 1rem;
}

.done {
  text-decoration: line-through;
}
</style>