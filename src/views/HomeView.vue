<script>
    import TodoForm from '@/components/TodoForm.vue';
    import TodoList from '@/components/TodoList.vue';
    import FilterSelect from '@/components/FilterSelect.vue';

    export default {
        components: {
            TodoForm,
            TodoList,
            FilterSelect
        },
        data() {
            return {
                todos: JSON.parse(localStorage.getItem('todos') || '[]'),
                filterCategory: 'All'
            }
        },
        computed: {
            filteredTodos() {
                if (this.filterCategory === 'All') return this.todos
                return this.todos.filter(t => t.category === this.filterCategory)
            },
        },
        watch: {
            todos: {
                handler(newVal) {
                    localStorage.setItem('todos', JSON.stringify(newVal))
                },
                deep: true
            }
        },
        methods: {
            addTodo(todo) {
                this.todos.push(todo)
            },
            toggleTodo(id) {
                const todo = this.todos.find(t => t.id === id);
                if(todo) todo.completed = !todo.completed
            },
            deleteTodo(id) {
                this.todos = this.todos.filter(t => t.id !== id)
            }
        }
    }
</script>

<template>
    <div>
        <TodoForm @add-todo="addTodo" />
        <FilterSelect v-model="filterCategory" />
        <TodoList 
            :todos="filteredTodos"
            @toggle-todo="toggleTodo"
            @delete-todo="deleteTodo"
        />
    </div>
</template>