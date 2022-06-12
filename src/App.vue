<script setup>
// import HelloWorld from './components/HelloWorld.vue'

import { ref } from "vue";

const items = ref([
  {id: 1, label: 'Watch Netflix', done: false},
  {id: 2, label: 'Eat at McDonalds', done: false},
  {id: 3, label: 'Sit all day', done: false}
])

const newItem = ref('')

const markCompleted = (item) => {
  item.done = !item.done
}

const addItem = () => {
  items.value.push({
    id: items.value.length + 1,
    label: newItem.value,
    done: false
  })
  newItem.value = ''
}

</script>

<template>
  <div>
    <h1 class="text-3xl">My Undo List</h1>
    <!-- <HelloWorld msg="Hello Vue 3 + Vite" /> -->
    <form
      @submit.prevent="addItem"
    >
      <input 
        v-model="newItem"
        type="text" 
        class="border border-gray-300 rounded-md"
      >
      <button 
        class="bg-green-600 ml-4 py-2 px-4 text-bold text-white rounded-md"
      >
        +
      </button>
    </form>
    <ul>
      <li 
        v-for="(item, index) in items" 
        :key="item.id" 
        :class="{ 'line-through text-gray-400' : item.done }"
        @click="markCompleted(item)"
      >
        {{ item.label }}
      </li>
    </ul>
  </div>
</template>
