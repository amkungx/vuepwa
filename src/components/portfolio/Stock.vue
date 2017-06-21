<template>
    <div class="col-sm-6 col-md-4">
        <b-card header="Card header text" class="mb-3" :title="stock.name" :sub-title="'Price: ' + stock.price + ' | Quantity: ' + stock.quantity">
            <div class="float-left">
                <input type="number" class="form-control" placeholder="Quantity" v-model="quantity" :class="{danger: insufficientQuatity}">
            </div>
            <div class="float-right">
                <button class="btn btn-success" @click="sellStock" :disabled="insufficientQuatity || quantity <= 0">{{insufficientQuatity ? 'Not enough' : 'Sell'}}</button>
            </div>
        </b-card>
    </div>
</template>
<script>
import { mapActions } from 'vuex'
export default {
    props: ['stock'],
    data() {
        return {
            quantity: 0
        }
    },
    computed: {
        insufficientQuatity() {
            return this.quantity > this.stock.quantity
        }
    },
    methods: {
        ...mapActions({
            sellStockAction: 'sellStock'
        }),
        sellStock() {
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            }
            this.sellStockAction(order)
            this.quantity = 0;
        }
    }
}
</script>
<style>
.danger {
    border: 1px solid red;
}
</style>
