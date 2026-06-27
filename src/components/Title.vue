<script setup>
const titleText = '你好，Codex！'
</script>

<template>
  <!-- Render the primary page title as a focused, reusable component. -->
  <h1 class="title">{{ titleText }}</h1>
</template>

<style scoped>
.title {
  color: #1f2937;
  font-size: 2.5rem;
  font-weight: 700;
  line-height: 1.2;
  text-align: center;
}
</style>
