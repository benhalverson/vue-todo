<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.complete }">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      <router-link v-bind:to="`/provider/${todo.id}`">{{
        todo.title
      }}</router-link>
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>
<script>
export default {
  name: 'TodoItem',
  props: ['todo'],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>
<style scoped>
.todo-item {
  background: #4f4f4f;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #ffffff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
