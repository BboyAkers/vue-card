<template>
  <div id="app">
    <div id="template">
      <div>
        <div class='card-wrapper' ref="cardcontainer"></div>
      </div>
    </div>
    <form class="card-body" id="CreditCardDetails" name="CreditCardDetails" novalidate ref="form">
            <input name="full-name" placeholder="Credit Card Name" v-model="creditCard.CardHolderName"/>          
            <input name="CreditCardNumber" placeholder="Credit Card Number" v-model="creditCard.CardNumber"/>
            <div class="row">
                <label class="col-3">Expiration Date<em>*</em></label>
                <div class="col-2">
                    <input v-model="month" placeholder="Month" type="text" name="month"/>
                </div>

                <div class="col-2">
                    <input v-model="years" placeholder="Years" type="text" name="years"/>
                </div>
            </div>

            <input name="CVV" placeholder="CVV" v-model="creditCard.CardCVV"/>

            <input name="Zipcode" placeholder="Zip Code" v-model="creditCard.ZipCode" label="Zip Code"/>
        </form>
  </div>
</template>

<script>

import card from 'card';

export default {
  name: 'app',
  data () {
    return {
      creditCard: {
        CardHolderName: '',
        CardNumber: '',
        CardCVV: '',
        ZipCode: '',
      },
      month: "",
      years: "",
      expiry: "",
      expiryval: '',
    }
  },

  mounted() {
    this.card = new Card({
        form: this.$refs.form,
        container: this.$refs.cardcontainer,
        formSelectors: {
        nameInput: 'input[name="full-name"]',
        expiryInput: 'input[name="expiryval"]',
        cvcInput: 'input[name="CVV"]',
        numberInput: 'input[name="CreditCardNumber"]',
      }
    });
  },
}
</script>

<style>
</style>
