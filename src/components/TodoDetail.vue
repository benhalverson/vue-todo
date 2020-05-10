<template>
  <div>
    <Header />
    <h1>details view</h1>
    <div>Todo ID: {{ todoDetail.id }}</div>
    <div>Todo Title: {{ todoDetail.title }}</div>
    <div>Todo UserID: {{ todoDetail.userId }}</div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from '../components/layout/Header';
export default {
  name: 'TodoDetail',
  component: {
    Header
  },
  data() {
    return {
      id: this.$route.params.id,
      todoDetail: {}
    };
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/todos/${this.id}`)
      .then(res => (this.todoDetail = res.data))
      .catch(e => console.log(e));
  }
};
</script>
