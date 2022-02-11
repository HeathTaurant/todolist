<script setup>
import { ref } from 'vue';

const items = ref([
  '첫번째 목록',
  '두번째 목록'
])

function add() {
  const todoText = document.getElementById('todo-input').value

  items.value.push(todoText)
}
function remove(itemsIndex) {
  console.log('remove')
  items.value.splice(itemsIndex, 1)
  }
</script>

<template>
  <div class="todo-list">
    <h1 class="todo-list-h1">Todo List</h1>
    <div class="todo-list-add">
      <input 
        type="text" 
        name="" 
        id="todo-input" 
        placeholder="add Items"
      >
      <button type="button" @click="add()">추가</button>
    </div>
    <div class="todo-items">
      <div 
        v-for="(item, index) in items" 
        :key="index"
      >
        <div>{{index + 1}} - {{item}}</div>
        <button 
          type="button" 
          @click="remove(index)"
        >
          삭제
        </button>
      </div>
    </div>
</div>
</template>

<style>

.todo-list {
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

}

.todo-list .todo-list-h1 {
  font-size: 24px;
}

.todo-list .todo-list-add {
  display: flex;
}

.todo-list .todo-items {
  margin-top: 8px;
  display: flex;
  flex-direction: column;

}
.todo-list .todo-items > * {
  display: flex;
  justify-content: space-between;
  padding: 4px;
}

</style>
