<script>
export default {
  data() {
    return {
      text: "",
      category: "Category",
    };
  },
  methods: {
    submit() {
      if (!this.text.trim()) return;

      this.$emit("add-todo", {
        id: Date.now(),
        text: this.text,
        category: this.category,
        completed: false,
      });

      this.text = "";
    },
  },
};
</script>

<template>
  <form class="flex justify-between items-center gap-4" @submit.prevent="submit">
    <input
      type="text"
      v-model="text"
      placeholder="Insert your task..."
      class="border p-2" />

    <div class="flex items-center gap-2">
      <select v-model="category" class="border p-2">
        <option>Work</option>
        <option>Personal</option>
      </select>
      <button type="submit" class="bg-blue-500 text-white px-4 py-2">
        Add
      </button>
    </div>
  </form>
</template>
