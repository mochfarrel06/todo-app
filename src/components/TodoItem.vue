<script>
    export default {
        props: {
            todo: {
                type: Object,
                required: true
            }
        }
    }
</script>

<template>
    <li :class="{ 'line-trough text-gray-400' : todo.completed }" class="flex justify-between items-center border p-2">
        <div>
            <input type="checkbox" :checked="todo.completed" @change="$emit('toggle')" class="mr-2" />
            {{ todo.text }} {{ todo.category }}
        </div>

        <button @click="$emit('delete')" class="text-red-500">X</button>
    </li>
</template>