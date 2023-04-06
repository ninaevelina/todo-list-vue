<script setup lang="ts">

import { ref } from 'vue';
import { Todo } from '../models/Todo';

const description = ref("");
console.log(description);
console.log(description.value);



const emit = defineEmits(["addTodo"])


const handleSubmit = () => {
    emit('addTodo', description.value);
    description.value = "";
}



</script>

<template>
    <form @submit.prevent="handleSubmit">
        <input v-model="description" type="text"/>
        <button>+</button>
    </form>
</template>

