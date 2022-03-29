<template>
    <div>
        <h1 @click="add">{{ count }}</h1>
        <Rate v-model="score" theme="red"></Rate>
        <TodoList />
    </div>
</template>

<script setup>
import { ref } from "vue";
import TodoList from "../components/TodoList.vue"
import Rate from '../components/Rate.vue'
import { useMouse } from '../utils/mouse'

// 鼠标
let { x, y } = useMouse()

// 变量
let score = ref(2.5)

// 调用
let { count, add } = lejia()
// 方法
function update(num) {
    score.value = num
}
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