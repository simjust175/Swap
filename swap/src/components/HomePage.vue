<template>
  <v-container class="fill-height">
    <v-responsive class="align-center text-center fill-height">
      <total-container :total-amount="totalAmount" :currencySymbol="changeData.currency2.symbol" :rate="rate" v-if="totalAmount"/>
      <currency-form @get-initialized="getRate" @currencyEmitted="currencyChoice" :currency2="currencyProp" />
    </v-responsive>
  </v-container>
</template>

<script setup>
import { reactive, ref, computed } from 'vue';
const changeData = reactive({
  currency1: {},
  currency2: {}
})
let totalAmount = ref("");
let rate = ref("");
const API_KEY = import.meta.env.VITE_API_KEY;

const currencyChoice =(emittedCurrency) => {
  changeData[emittedCurrency.order] = emittedCurrency;
}

const getRate = async (amount) => {
  if (!amount) return "Error";
  const res = await fetch(`https://v6.exchangerate-api.com/v6/${API_KEY}/pair/${changeData.currency1.currency}/${changeData.currency2.currency}`);
  const {conversion_rate} = await res.json();
  rate.value = conversion_rate;
  totalAmount.value = conversion_rate * amount
}

const currencyProp = computed(()=> changeData.currency2.currency)
//
</script>

