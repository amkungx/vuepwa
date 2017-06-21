<template>
    <div class="row">
        <comStock v-for="stock in stocks" :stock="stock" :key="stock.id"></comStock>
    </div>
</template>
<script>
import {mapGetters} from 'vuex'
import Stock from './Stock'
export default {
  computed: {
      ...mapGetters({
          stocks: 'stockPortfolio'
      })
  },
  components: {
      comStock: Stock
  }
}
</script>
<style>

</style>
