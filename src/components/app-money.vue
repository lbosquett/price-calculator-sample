<script setup>
const props = defineProps(['value']);

function formatMoney(value) {
  return `${value.toFixed(2)}`;
}
</script>

<template>
  <span class="text-green-600">
    $ <span class="font-mono">
      {{ formatMoney(props.value) }}
    </span>
  </span>

</template>

<style scoped>

</style>