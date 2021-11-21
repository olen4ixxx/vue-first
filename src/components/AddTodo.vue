<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button class="submit">Create</button>
  </form>
</template>

<script>
export  default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      console.log('Submit', this.title)
      if (this.title.trim()) {
        const  NewTodoElement = {
          id: Date.now(),
          title: this.title,
          completed: false
        }
        this.$emit('add-todoElement', NewTodoElement)
        this.title =''
      }
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
}
input {
  width: 400px;
}
</style>
