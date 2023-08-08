<script setup lang="ts">

import { ref } from 'vue'

defineProps<{}>()

const list_todo = ref<string[]>([]);
const todo_input = ref('');


function add_todo(){
    list_todo.value.push(todo_input.value)
    console.log(`added to-do, ${todo_input.value}...`);

    todo_input.value = '';
}

function removeToDo(todo_index:number){
    console.log('Remove to-do')
    list_todo.value.splice(todo_index, 1);

}


</script>

<template>
    <div class="container">
        <form>
            <input
            class="input-todo input-todo-text"
            type="text"
            v-model="todo_input" 
            placeholder="write todo"
            >

            <button
            class="input-todo input-todo-submit"
            type="button"
            @click="add_todo"
            >add to-do</button>

        </form>

        <ul v-if="list_todo.length">
            <li v-for="(item,index) in list_todo">
                {{ item }} 
                <button class="button-remove-todo" @click="removeToDo(index)">x</button>
            </li>
        </ul>
    </div>
    
</template>


<style >

form {
    display: flex; 
    gap: 1rem;
}
.input-todo{
    padding:5px 10px;
    border-radius: 3px;
}

.button-remove-todo{
    color:var(--button-action);
    font-weight: 600;
    background-color: transparent;
    border:none;
    cursor: pointer;

}

.button-remove-todo:hover{
    background-color: var(--button-action);
    color:var(--color-text);
}

.input-todo-text{
    background-color: transparent;
    border:1px solid var(--button-action);
    color:var(  --color-text);
   outline: none;
}

.input-todo-submit{
   background-color:var( --button-action);
   border:none;
}

.input-todo-submit:hover{
   background-color:var( --button-action-hover);
}

</style>