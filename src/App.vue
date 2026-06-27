<script setup>
import Title from './components/Title.vue'
</script>

<template>
  <main class="app">
    <!-- Keep the startup page focused on the reusable Title component. -->
    <Title />
  </main>
</template>

<style scoped>
.app {
  align-items: center;
  display: flex;
  min-height: 100vh;
  justify-content: center;
  width: 100%;
}
</style>
