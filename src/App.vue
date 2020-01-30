<template>
<div id="app">
    <Checkout size="md" :rounded="true" api_key="wtd8ulyjfghMPuEtRE0Q_300c7b5a0b7e4fe7bdf49d901c8779d5" :amount="amount" request_type="collect" :transaction_ref="transaction_ref" :customer="customer" :options="options" :meta="meta" :details="details" :callback="onCallback" :close="onClose"> Pay Now </Checkout>
</div>
</template>

<script>
/* eslint-disable */
import Checkout from './components/Checkout.vue'

export default {
    name: 'app',
    props: ['api_key'],
    components: {
        Checkout
    },
    created(){
        console.log(this);
    },
    mounted(){
        // console.log(this);
    },
    data() {
        return {
            transaction_ref: Math.floor((Math.random() * 1434)) + '78805' + Math.floor((Math.random() * 4543)), //generate a unique number
            transaction_desc: 'demo payment',
            transaction_ref_parent: "",
            amount: 5000, // in kobo
            options: null,
            meta: null,
            details: null,
            customer: {
                customer_ref: '2347065514172', //how you identify the customer
                firstname: 'Demo',
                surname: 'Customer',
                email: 'samuel@onepipe.io',
                mobile_no: '2347065514172'
            },
        }
    },
    methods: {
      onCallback(res){
        console.log(res);
      },
      onClose(res){
        console.log(res);
      }
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
