<script setup lang="ts">
import { Todo } from '../models/Todo';


interface IDisplayTodosProps {
    todo: Todo;
}

defineProps<IDisplayTodosProps>();
defineEmits(["toggleTodo"]);

</script>

<template>
      
        <div class="new">
            <div @click="() => $emit('toggleTodo')" :class="todo.completed ? 'completed' : ''" v-if="!todo.completed" class="incompleted"> {{ todo.description }} 
           <button v-if="!todo.completed" :class="todo.completed" class="check">&#10003;</button>
        </div>
        </div>
       <div class="completed">
        <div v-if="todo.completed" class="done"> {{ todo.description }}</div>
       </div>
       
    
</template>

<style scoped>

.new {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
}
.incompleted {
    background-color: red;
    display: flex;
    flex-wrap: wrap;
}
.done {
    background-color: green;
    text-decoration: line-through;
}

.completed {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
}
.check {
    float: right;
}

</style>