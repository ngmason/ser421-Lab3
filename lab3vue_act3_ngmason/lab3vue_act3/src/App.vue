<script>
import Balance from './components/Balance.vue'
import HelloWorld from './components/HelloWorld.vue'
import Currency from './components/Currency.vue'

export default {
  data() {
    return {
      fname: "Nina",
      bal: 25,
      balanceCurrency: "USD"
    }
  },
  components: {
    Balance,
    HelloWorld,
    Currency
  },
  methods: {
    updateBalance(newBalance) {
      this.bal = newBalance;
    },
    updateCurrency(newCurrency) {
      this.balanceCurrency = newCurrency;
    }
  }
}
</script>

<template>
  <header>
    <div class="wrapper">
      <HelloWorld :name="fname"/><br>
      <Balance :balance="bal" :currency="balanceCurrency" @newBal="updateBalance"/><br>
      <Currency :defaultAmount="bal" :fromCurrency="balanceCurrency" @updateCurrency="updateCurrency"/>
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 4);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
