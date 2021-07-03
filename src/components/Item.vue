<template>
  <div class="todo-item" :class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" @change="markComplete" :checked="todo.completed">
      {{todo.title}}
      <button  class="del" @click="$emit('dele-todo',todo.id)">x</button>
      </p>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: ["todo"], 
  methods: {
     markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
  .todo-item {
    background: #94d2bd;
    padding: 10px;
    border-bottom: 1px #52b69a dotted;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: #370617;
    color: #f77f00;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>

