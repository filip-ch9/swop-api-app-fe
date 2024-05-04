<template>
  <div class="container">
    <h1>Exchange Rates</h1>
    <div>
      <label class="label" for="sourceCurrency">Source Currency:</label>
      <input class="input" type="text" id="sourceCurrency" v-model="sourceCurrency">
    </div>
    <div>
      <label class="label" for="targetCurrency">Target Currency:</label>
      <input class="input" type="text" id="targetCurrency" v-model="targetCurrency">
    </div>
    <div>
      <label class="label" for="amount">Amount:</label>
      <input class="input" type="number" id="amount" v-model.number="amount">
    </div>
    <button class="button" @click="fetchCurrencyData">Get Exchange Rate</button>

    <div v-if="currencyResponse" class="result">
      <p>Source Currency: {{ currencyResponse.sourceCurrency }}</p>
      <p>Target Currency: {{ currencyResponse.targetCurrency }}</p>
      <p>Amount: {{ amount }}</p>
      <p>Result: {{ currencyResponse.monetaryValue }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { createToaster } from "@meforma/vue-toaster";

const toaster = createToaster({ });

export default {
  data() {
    return {
      sourceCurrency: '',
      targetCurrency: '',
      amount: null,
      currencyResponse: null
    };
  },
  methods: {
    fetchCurrencyData() {
      axios.get(`http://localhost:9090/api/currency/exchange?source_currency=${this.sourceCurrency}&target_currency=${this.targetCurrency}&amount=${this.amount}`, {
      }).then(response => {
            this.currencyResponse = response.data;
          })
          .catch(error => {
            toaster.error(error.response.data.message, {
              position: "top",
            })
          });
    }
  }
};
</script>

<style>
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.label {
  display: block;
  margin-bottom: 10px;
}

.input {
  width: 100%;
  padding: 8px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

.button:hover {
  background-color: #45a049;
}

.result {
  margin-top: 20px;
  padding: 10px;
  background-color: #f0f0f0;
  border-radius: 5px;
}
</style>
