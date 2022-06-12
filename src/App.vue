<script setup>

import AddItemsForm from './components/AddItemsForm.vue'
import ItemsTemplate from './components/ItemsTemplate.vue'

import { ref } from "vue";

const items = ref([
  {id: 1, label: 'Watch Netflix', done: false},
  {id: 2, label: 'Eat at McDonalds', done: false},
  {id: 3, label: 'Sit all day', done: false}
])


const markCompleted = (item) => {
  item.done = !item.done
}

const addItem = (newItem) => {
  items.value.push({
    id: items.value.length + 1,
    label: newItem.value,
    done: false
  })
  newItem.value = ''
}

</script>

<template>
  <div class="w-5/6 md:w-1/2">
    <h1 class="text-4xl text-center py-8">My Undo List</h1>

    <add-items-form @add-item="addItem"></add-items-form>

    <items-template :items="items" @done="markCompleted"></items-template>

  </div>
</template>
