<template>
    <div>
        <img src="../assets/logo.png" alt="Vue.js PWA">
        <h1>Trade of view your Portfolio</h1>
        <h6>You nay Save & Load your Data</h6>
        <h6>Click on 'End Day' to begin the New Day!</h6>
        <hr>
        <p>Your funds: {{funds | currency}}</p>

        <b-card class="mb-2" variant="success">
            <span @click="print"><icon name="gear" spin></icon></span>
            <icon name="vue" spin scale="3"></icon>
            <icon name="webpack" spin scale="3"></icon>
        </b-card>

    </div>
</template>
<script>
export default {
    methods: {
        print() {
            console.log(this)
        }
    },
    computed: {
        funds() {
            return this.$store.getters.funds
        }
    }
}
</script>
<style>

</style>
