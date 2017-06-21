<template>
    <div>
        <b-navbar toggleable type="inverse" variant="success">
    
            <b-nav-toggle target="nav_collapse"></b-nav-toggle>
    
            <b-link class="navbar-brand" to="/">
                <span>BootstrapVue</span>
            </b-link>
    
            <b-collapse is-nav id="nav_collapse">
    
                <b-nav is-nav-bar>
                    <b-nav-item to="/portfolio">Portfolio</b-nav-item>
                    <b-nav-item to="/stocks">Stocks</b-nav-item>
                    <b-nav-item>Contact Us</b-nav-item>
                </b-nav>
    
                <b-nav is-nav-bar class="ml-auto">
    
                    <!-- Navbar dropdowns -->
                    <b-nav-item right @click="endDay">End Day</b-nav-item>
                    <b-nav-item-dropdown right>
    
                        <!-- Using text slot -->
                        <template slot="text">
                            <span>Save & Load</span>
                        </template>
    
                        <b-dropdown-item @click="saveData">Save Data</b-dropdown-item>
                        <b-dropdown-item @click="loadData">Load Data</b-dropdown-item>
                    </b-nav-item-dropdown>
                    <b-nav-item right>
                        <b style="color:white">Funds: {{funds | currency}}</b>
                    </b-nav-item>
    
                </b-nav>
            </b-collapse>
        </b-navbar>
    </div>
</template>
<script>
import { mapActions } from 'vuex'
export default {
    computed: {
        funds() {
            return this.$store.getters.funds
        }
    },
    methods: {
        ...mapActions({
            ramdomizeStocks: 'ramdomizeStocks',
            loadDataAction: 'loadData'
        }),
        endDay() {
            this.ramdomizeStocks()
        },
        saveData() {
            const data = {
                funds: this.$store.getters.funds,
                stockPortfolio: this.$store.getters.stockPortfolio,
                stocks: this.$store.getters.stocks
            }
            this.$http.put('data.json', data)
        },
        loadData() {
            this.loadDataAction()
        }
    }
}
</script>
<style>

</style>
