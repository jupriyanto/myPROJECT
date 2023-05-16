<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(true)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <div class="text-center ">
    <h1 class="text-4xl py-5">DATA LIST</h1>
    <form class="max-w-md mx-auto p-4 rounded-lg shadow-md bg-white" @submit.prevent="addTodo">
      <input class="my-3 border rounded w-full py-2 px-3 text-gray-700 focus:outline-none focus:shadow-outline" placeholder="masukkan data list" v-model="newTodo">
      <button class="border my-3 rounded-lg bg-teal-600 p-2.5 font-medium text-sm text-white hover:bg-teal-400">Tambah list</button>
    </form>
    <div class="py-5 max-w-md mx-auto">
      <ul class="list-none flex-row mx-auto">
        <div class="">
          <li class="py-2 flex items-center justify-center bg-sky-400 rounded-lg my-3" v-for="todo in filteredTodos" :key="todo.id">
              <input type="checkbox" v-model="todo.done" class=" border rounded w-5 h-5 mr-5 py-2 px-3 h-4 w-4">
              <span :class="{ done: todo.done }">{{ todo.text }}</span>
              <button class="ml-5 bg-red-500 hover:bg-red-400 text-white font-bold py-0.5 px-2 rounded-full" @click="removeTodo(todo)">X</button>
            </li>
        </div>
      </ul>
    </div>
    <button class="border my-3 rounded-lg bg-teal-600 p-2.5 font-medium text-sm text-white hover:bg-teal-400" @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Show all' : 'Tampilkan yang belum selesai' }}
    </button>
  </div>
</template>

<style>
.done {
  text-decoration: line-through;
}
</style>