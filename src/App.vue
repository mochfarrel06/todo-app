<template>
  <div class="font-rubik flex flex-col h-screen p-4">
    <main class="flex-1 bg-white overflow-auto">
      <RouterView />
    </main>
  </div>
</template>

<script setup>
  import { RouterView } from 'vue-router';
</script>

<style scoped>
  main {
    width: 800px;
    margin: 5rem auto;
  }
</style>