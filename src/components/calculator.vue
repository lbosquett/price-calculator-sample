<script setup>
import {computed, reactive, ref} from "vue";
import CompoundPrice from "./compound-price.vue";
import AppPlanItem from "./app-plan-item.vue";
import AppMoney from "./app-money.vue";

const pagesCount = ref(0);
const hasSupport = ref(false);
const services = reactive({
  email: false,
  sms: false
});

const servicesValue = reactive({
  pages: {initial: 700, monthly: 20},
  support: {initial: 0, monthly: 100},
  services: {
    email: {initial: 100, monthly: 5},
    sms: {initial: 100, monthly: 25}
  },
});

const total = computed(() => {
  return {
    initial: (pagesCount.value > 0 ? servicesValue.pages.initial : 0)
        + (hasSupport.value ? servicesValue.support.initial : 0)
        + (services.email ? servicesValue.services.email.initial : 0)
        + (services.sms ? servicesValue.services.sms.initial : 0),
    monthly: (pagesCount.value * servicesValue.pages.monthly)
        + (hasSupport.value ? servicesValue.support.monthly : 0)
        + (services.email ? servicesValue.services.email.monthly : 0)
        + (services.sms ? servicesValue.services.sms.monthly : 0)
  };
});

</script>

<template>
  <div class="calculator-grid grid grid-cols-2">
    <div>
      <h1 class="text-3xl">Plan 📌</h1>

      <app-plan-item title="How many web pages? 😁" :service="servicesValue.pages">
        <input type="number" v-model="pagesCount" />
      </app-plan-item>

      <div class="mt-4">
        <h4 class="mb-4 text-2xl">Services</h4>

        <app-plan-item title="send e-mail ✉️" :service="servicesValue.services.email">
          <input type="checkbox" v-model="services.email"/>
        </app-plan-item>

        <app-plan-item title="send sms" :service="servicesValue.services.sms">
          <input type="checkbox" v-model="services.sms"/>
        </app-plan-item>
      </div>

      <app-plan-item title="24h support? 🦉" :service="servicesValue.services.sms">
        <input type="checkbox" v-model="hasSupport" />
      </app-plan-item>
    </div>
    <div>
      <div>
        <h4 class="text-2xl">Total 💰</h4>
        <div class="text-xl mt-4">
          initial of <app-money :value="total.initial" />,
        </div>
        <div class="text-xl">
          then <app-money :value="total.monthly" /> per month
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.calculator-grid {
  grid-template: 1fr / 60% auto;
  gap: 15px;
}
</style>