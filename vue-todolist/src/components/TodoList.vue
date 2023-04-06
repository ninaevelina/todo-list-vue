<script setup lang="ts">
import { ref } from 'vue'
import { Todo } from '../models/Todo';
import SubmitTodo from './SubmitTodo.vue';
import DisplayTodos from './DisplayTodos.vue';



const todos = ref<Todo[]>(JSON.parse(localStorage.getItem("todos") || "[]"));

//const userInput = ref("");

function setToLS(todos: Todo[]) {
    localStorage.setItem("todos", JSON.stringify(todos));
}


const submitTodo = (description: string) => {
    todos.value.push(new Todo(description, false));
    setToLS(todos.value);
    
    
    
    
}

const toggleTodo = (i: number) => {
    todos.value[i].completed = !todos.value[i].completed
    console.log("toggletodo", i);
    setToLS(todos.value)
    console.log(todos);
}




</script>


<template>

    <SubmitTodo @add-todo="submitTodo"></SubmitTodo>
    <div class="list">
    <DisplayTodos :todo="todo" v-for="(todo, index) in todos" @toggle-todo="() => toggleTodo(index)" :key="index"></DisplayTodos>
    </div>



</template>

<style scoped>
/*
.list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    flex-direction: column;
    gap: 20px;
    margin-top: 50px;

}*/

</style>