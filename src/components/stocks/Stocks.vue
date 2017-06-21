<template>
    <div class="row">
        <comStock v-for="stock in stocks" :stock="stock" :key="stock.id"></comStock>
    </div>
</template>
<script>
import Stock from './Stock'
export default {
    components: {
        comStock: Stock
    },
    computed: {
        stocks() {
            return this.$store.getters.stocks
        }
    }
}
</script>
<style>

</style>
