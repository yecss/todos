<template>
  <div class="container">
    <h1 class="title">TodoList</h1>
    <todoList class="child"></todoList>
  </div>
</template>

<script>
import todoList from "./components/todo-list.vue";
export default {
  name: "App",
  components: {
    todoList,
  },
};
</script>

<style scoped>
.container {
  height: 100vh;
  background-color: #eff0f3;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.child {
  width: 100%;
}
.title {
  color: #0d0d0d;
  margin-bottom: 30px;
}
</style>