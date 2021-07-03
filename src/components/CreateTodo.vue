<template>
  <div>
    <form @submit.prevent="CreateTodo">
      <input type="text" v-model="title" name="title" placeholder="Create Todo">
      <input type="submit" value="Submit" class="btn" style="background:#013a63;">
    </form>
  </div>
</template>

<script>
// import uuid from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    CreateTodo() {
      const todo = {
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('create-todo', todo);  // i use  @dele-todo = "deleteTodo" in home and pass todo in emit to create new one

      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding:13px;
  }

  input[type="submit"] {
    flex: 2;
  }
</style>


