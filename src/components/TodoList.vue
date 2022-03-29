<template>
    <div>
        <input type="text" v-model="title" @keydown.enter="addTodo" />
        <button v-if="active < all" @click="clear">清理</button>
        <ul v-if="todos.length">
            <li v-for="todo in todos">
                <input type="checkbox" v-model="todo.done" />
                <span :class="{ done: todo.done }">{{ todo.title }}</span>
            </li>
        </ul>
        <div v-else>暂无数据</div>
        <div>
            全选
            <input type="checkbox" v-model="allDone" />
            <span>{{ active }} / {{ all }}</span>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from "vue";
import { useStorage } from '../utils/storage.js'

// 调用
let { title, todos, addTodo, clear, active, all, allDone } = useTodos();

// 方法
function useTodos() {
    // 变量
    let title = ref("");
    let todos = useStorage('todos', []);

    // 方法
    function addTodo() {
        todos.value.push({
            title: title.value,
            done: false,
        });
        title.value = "";
    }
    function clear() {
        todos.value = todos.value.filter((v) => !v.done);
    }
    // 计算属性
    let active = computed(() => {
        return todos.value.filter((v) => !v.done).length;
    });
    let all = computed(() =>
        todos.value.length
    );
    let allDone = computed({
        get: function () {
            return active.value === 0;
        },
        set: function (value) {
            todos.value.forEach((todo) => {
                todo.done = value;
            });
        },
    });
    // 返回
    return { title, todos, addTodo, clear, active, all, allDone };
}

</script>