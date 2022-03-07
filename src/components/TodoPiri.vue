<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});

const newPiri = ref("");
const todos = ref([]);

function addPiri() {
  todos.value.push({ text: newPiri.value, done: false });
  newPiri.value = "";
}

function removePiri(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <input v-model="newPiri" @keyup.enter="addPiri" />
  <button @click="addPiri">Add</button>
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      <input type="checkbox" v-model="todo.done" />
      <span :class="{ done: todo.done }"> {{ todo.text }}</span>
      <button @click="removePiri(todo)">x</button>
    </li>
  </ul>
</template>
              
<style scoped>



li {
  list-style: none;
  display: flex;
  margin-bottom: 5px;
  justify-content: space-between;
  width: 25%;
  font-weight: bold;
  font-size: 20px;
  border: solid 1px;
}
  

.done {
  text-decoration: line-through;
  opacity: 0.5;
}

ul {
  display: flex;
  justify-content: center;
 flex-direction: column;
 align-items: center;
 margin-right: 45px;
  
}


</style>
