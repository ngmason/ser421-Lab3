<script>
export default {
    name: 'Balance',
    props: {
      balance: {
        type: Number,
        required: true
      },
      currency: {
        type: String,
        required: true
      }
    },
    data() {
        return {
            amount: 10
        }
    },
    emits: ['newBal'], 
    computed: {
        balanceString() {
            return `Account Balance: ${this.balance}`;
        },

        canSubtract() {
          return this.amount <= this.balance;
        }
    },
    methods: {
        addBalance() {
            const newBalance = this.balance + this.amount;
            this.$emit('newBal', newBalance);
        },
        subtractBalance() {
            if (this.canSubtract) {
              const newBalance = this.balance - this.amount;
              this.$emit('newBal', newBalance);
            }
        }
    },
    mounted() {
        console.log('Application mounted');
    },
}
</script>

<template>
    <div class="greetings">
      <h3>{{balanceString}} {{currency}}, Amount: {{amount}} {{currency}}</h3><br>
      <input id="amount" type="range" v-model.number="amount" min="5" max="100" step="5"/>
      <button @click="addBalance">Add</button><button @click="subtractBalance" :disabled= "!canSubtract" >Subtract</button>
    </div>
  </template>
  
  <style scoped>
  h1 {
    font-weight: 500;
    font-size: 2.6rem;
    top: -10px;
  }
  
  h3 {
    font-size: 1.2rem;
  }
  
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
  
  @media (min-width: 1024px) {
    .greetings h1,
    .greetings h3 {
      text-align: left;
    }
  }
  </style>
