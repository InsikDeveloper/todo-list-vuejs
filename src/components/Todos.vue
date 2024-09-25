<template>
  <div>
    <ul v-if="todos && todos.length > 0">
      <li
        class="flex justify-between"
        v-for="(todo, index) in todos"
        :key="index"
      >
        <span class="font-bold px-3">{{ todo }}</span>
        <div class="space-x-5">
          <button
            class="py-2 px-3 border-[1px] border-sky-600 border-solid rounded-lg hover:bg-sky-600 hover:text-white duration-200"
            @click="editTodo(index)"
          >
            Edit
          </button>
          <button
            class="py-2 px-3 border-[1px] border-red-600 border-solid rounded-lg hover:bg-red-600 hover:text-white duration-200"
            @click="deleteTodo(index)"
          >
            Del
          </button>
        </div>
      </li>
    </ul>
    <p class="px-3 font-bold" v-else>No todos available.</p>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  todos: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits();

const deleteTodo = (index) => {
  emit("delete-todo", index);
};

const editTodo = (index) => {
  emit("edit-todo", index);
};
</script>
