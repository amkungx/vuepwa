<template>
    <div class="col-sm-6 col-md-4">
        <b-card header="Card header text" class="mb-3" :title="stock.name" :sub-title="'Price: ' + stock.price">
            <div class="float-left">
                <input type="number" class="form-control" placeholder="Quantity" v-model="quantity" :class="{danger: insufficientFunds}">
            </div>
            <div class="float-right">
                <button class="btn btn-success" @click="buyStock" :disabled="insufficientFunds || quantity <= 0">{{insufficientFunds ? 'Insufficient Funds' : 'Buy'}}</button>
            </div>
        </b-card>
    </div>
</template>
<script>
export default {
    props: ['stock'],
    data() {
        return {
            quantity: 0
        }
    },
    computed: {
        funds() {
            return this.$store.getters.funds
        },
        insufficientFunds() {
            return this.quantity * this.stock.price > this.funds
        }
    },
    methods: {
        buyStock() {
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            };
            console.log(order);
            this.$store.dispatch('buyStock', order)
            this.quantity = 0;
        }
    }
}
</script>
<style scoped>
.danger {
    border: 1px solid red;
}
</style>
