<script setup>
import CompoundPrice from "./compound-price.vue";

const props = defineProps(['title', 'service'])
</script>

<template>
  <div class="mt-4 bg-gray-50 rounded-xl p-4">
    <div>{{ props.title }}</div>
    <compound-price :service="props.service"/>
    <div class="mt-2">
      <slot></slot>
    </div>
  </div>
</template>