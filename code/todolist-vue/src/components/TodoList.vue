<script setup>
import { ref } from 'vue';

const items = ref([
  '첫번째 목록',
  '두번째 목록',
  '세번째 목록',
  '네번째 목록',
  '다섯번째 목록',
])

function add() {
  const todoText = document.getElementById('todo-input').value

  items.value.push(todoText)
}

function remove(itemsIndex) {
  items.value.splice(itemsIndex, 1)
}
</script>

<template>
    <div 
        class="
            max-w-xl
            max-h-96
            w-full 
            h-full
        "
    >
        <div 
            :class="[
                'bg-gray-50 border border-gray-200 rounded shadow-lg',
                'divide-y divide-gray-200'
            ]"
        >
            <div class="bg-indigo-500 text-white p-4 rounded-tl rounded-tr">
                <h1 class="text-xl italic">Todo List</h1>
            </div>
            <div class="flex flex-col p-4">
                <div class="flex space-x-2">
                    <div class="flex-1">
                        <input 
                            class="w-full rounded-sm border-gray-300 text-sm"
                            type="text" 
                            id="todo-input" 
                            placeholder="add Items"
                        >
                    </div>
                    <button 
                        class="bg-indigo-500 rounded-sm text-white text-sm px-4"
                        type="button" 
                        @click="add()"
                    >
                        추가
                    </button>
                </div>
            </div>
            <div
                class="flex flex-col space-y-2 p-4"
            >
                <div 
                    :class="[
                        'flex items-center justify-between',
                        'bg-white border birder-gray-200 rounded-lg',  
                        'p-3'
                    ]"
                    v-for="(item, index) in items" 
                    :key="index"
                >
                    <div class="flex-1">
                        <p class="overflow-gidden break-words">{{ index + 1 }} - {{ item }}</p>
                    </div>
                    <button 
                        class="bg-red-500 text-white rounded-sm py0-2 px-4 text-sm ml-4"
                        type="button" 
                        @click="remove(index)"
                    >
                    삭제
                    </button>
                    <!--lorem-->

                </div>
            </div>
        </div>
    </div>
</template>