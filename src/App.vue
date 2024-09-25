<template>
  <div class="min-h-screen w-full flex justify-center items-center text-xl">
    <div class="w-1/2 shadow-xl p-5">
      <h1 class="text-3xl font-bold -tracking-tight text-center mb-5">
        Todo List
      </h1>
      <div class="flex gap-3 justify-between mb-5">
        <input
          class="w-[85%] py-2 px-3 bg-blue-300/30"
          type="text"
          v-model="newTodo"
          placeholder="Enter a new todo"
        />
        <button
          class="py-2 px-3 border-[1px] border-green-600 border-solid rounded-lg hover:bg-green-600 hover:text-white duration-200"
          @click="addTodo"
        >
          Add Todo
        </button>
      </div>
      <div>
        <Todos :todos="todos" @delete-todo="deleteTodo" @edit-todo="editTodo" />
      </div>
    </div>
  </div>
</template>

<script setup>
import Todos from "./components/Todos.vue";
import { ref } from "vue";

const todos = ref([]);
const newTodo = ref("");

const addTodo = () => {
  const trimmedTodo = newTodo.value.trim();
  if (trimmedTodo) {
    todos.value.push(trimmedTodo);
    newTodo.value = "";
  }
};

const deleteTodo = (index) => {
  todos.value.splice(index, 1);
};
const editTodo = (index) => {
  const editedTodo = prompt("Edit Todo", todos.value[index]);
  const trimmedTodo = editedTodo ? editedTodo.trim() : "";

  if (trimmedTodo) {
    todos.value[index] = trimmedTodo;
  }
};
</script>
