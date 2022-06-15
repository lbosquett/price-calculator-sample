<script setup>
import AppMoney from "./app-money.vue";

const props = defineProps(['service']);
</script>

<template>
  <div>
    initial of <app-money :value="props.service.initial" />,
    then <app-money :value="props.service.monthly" /> per month
  </div>
</template>