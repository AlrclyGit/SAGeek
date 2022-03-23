<template>
    <div>
        <h1 @click="add">{{ count }}</h1>
        <TodoList />
    </div>
</template>

<script setup>
import TodoList from "../components/TodoList.vue"
import { useMouse } from '../utils/mouse'

import { ref } from "vue";

let { x, y } = useMouse()

let { count, add } = lejia()

function lejia() {
    const count = ref(1)
    function add() {
        count.value++
    }
    return { count, add };
}

</script>

<style scoped>
h1 {
    color: red;
}
</style>