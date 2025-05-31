<script>
import { BookOpenIcon } from "@heroicons/vue/24/solid";
import TodoForm from "@/components/TodoForm.vue";
import TodoList from "@/components/TodoList.vue";
import FilterSelect from "@/components/FilterSelect.vue";

export default {
  components: {
    TodoForm,
    TodoList,
    FilterSelect,
    BookOpenIcon,
  },
  data() {
    return {
      todos: JSON.parse(localStorage.getItem("todos") || "[]"),
      filterCategory: "All",
    };
  },
  computed: {
    filteredTodos() {
      if (this.filterCategory === "All") return this.todos;
      return this.todos.filter((t) => t.category === this.filterCategory);
    },
  },
  watch: {
    todos: {
      handler(newVal) {
        localStorage.setItem("todos", JSON.stringify(newVal));
      },
      deep: true,
    },
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    toggleTodo(id) {
      const todo = this.todos.find((t) => t.id === id);
      if (todo) todo.completed = !todo.completed;
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
  },
};
</script>

<template>
  <div class="flex flex-col gap-20">
    <div class="flex justify-center">
      <h1 class="text-4xl font-bold flex items-center gap-4 text-gray-700">
        <span>To-Do List</span>
        <BookOpenIcon class="w-10 h-10 text-gray-700" />
      </h1>
    </div>

    <div class="flex flex-col gap-4">
      <TodoForm @add-todo="addTodo" />
      <FilterSelect v-model="filterCategory" />
      <TodoList
        :todos="filteredTodos"
        @toggle-todo="toggleTodo"
        @delete-todo="deleteTodo" />
    </div>
  </div>
</template>
