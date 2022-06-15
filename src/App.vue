<script setup>
import Calculator from "./components/calculator.vue";
import AppHeader from "./components/layout/app-header.vue";
</script>

<template>
  <div class="header-container">
    <div class="page-800">
      <app-header />
    </div>
  </div>
  <div class="page-800">
    <calculator />
  </div>
</template>

<style scoped>
.page-800 {
  width: clamp(600px, 800px, 100%);
  margin: 0 auto;
}

.header-container {
  height:100px;
  border-bottom: 1px solid #f4f4f4;
  margin-bottom: 20px;
}
</style>
