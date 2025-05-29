<template>
  <div class="p-4">
    <nav class="flex gap-4">
      <RouterLink to="/">Home</RouterLink>
    </nav>

    <RouterView />
  </div>
</template>

<script setup>
  import { RouterLink, RouterView } from 'vue-router';
</script>