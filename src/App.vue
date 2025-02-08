<template>
  <div class="container">
    <h1>To-Do List</h1>
    <TodoSimpleForm @add-todo="addTodo" />

    <div v-if="!todos.length">추가된 Todo가 없습니다.</div>
    <TodoList :todos="todos" @toggle-todo="ToggleTodo" />
  </div>
</template>
<script>
import { ref } from "vue";
import TodoSimpleForm from "./components/TodoSimpleForm.vue";
import TodoList from "./components/TodoList.vue";
export default {
  components: {
    TodoSimpleForm,
    TodoList,
  },
  setup() {
    const toggle = ref(false);
    const todoStyle = {
      textDecoration: "line-through",
      color: "gray",
    };
    const todos = ref([]);

    const onToggle = () => {
      toggle.value = !toggle.value;
    };
    const deleteTodo = index => {
      todos.value.splice(index, 1);
    };

    const ToggleTodo = index => {
      console.log(todos.value[index]);

      todos.value[index].completed = !todos.value[index].completed;
      console.log(todos.value[index]);
    };
    // const updateName = e => {
    //   name.value = e.target.value;
    // };

    const addTodo = todo => {
      todos.value.push(todo);
    };
    return {
      todos,
      onToggle,
      todoStyle,
      deleteTodo,
      addTodo,
      ToggleTodo,
      //updateName,
    };
  },
};
</script>

<style>
.todo {
  color: gray;
  text-decoration: line-through;
}
</style>
