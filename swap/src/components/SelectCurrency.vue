
<template>
  <v-select :label="direction" :items="items" :item-props="itemProps" v-model="selectedCurrency" ></v-select>
</template>

<script>
  export default {
    props:{
      order: String
    },
    data: () => ({
      selectedCurrency: "",
      items: [
        {
        symbol: '$',
        currency: 'USD',
      },
      {
        symbol: '₪',
        currency: 'ILS',
      },
      {
        symbol: '€',
        currency: 'EUR',
      },

      {
        symbol: '£',
        currency: 'GBP',
      },
      {
        symbol: '₣',
        currency: 'CHF'
      },
      {
        symbol: 'AUD',
        currency: 'AUD'
      },
      {
        symbol: 'CAD',
        currency: 'CAD'
      }
       
      ],
    }),
    computed:{
      direction(){return this.order === "currency1" ? "From:" : "To:"},
    },
    methods: {
      itemProps (item) {
        return  {
          title: item.currency,
          subtitle: item.symbol,
        }
    },
  },
    watch: {
      selectedCurrency(newCurrency){
        this.$emit("currencyEmitted", {order: this.order, currency: newCurrency.currency, symbol: newCurrency.symbol})
      }
    }
  }
</script>