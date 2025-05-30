<script>
    import TodoItem from './TodoItem.vue';

    export default {
        components: {
            TodoItem
        },
        props: {
            todos: {
                type: Array,
                required: true
            }
        }
    }
</script>

<template>
    <ul class="space-y-2">
        <TodoItem 
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
            @toggle="() => $emit('toggle-todo', todo.id)"
            @delete="() => $emit('delete-todo', todo.id)"
        />
    </ul>
</template>