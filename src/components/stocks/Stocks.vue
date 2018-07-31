<template>
    <div>
        <Stock v-for="stock in stocks" :stock="stock"></Stock>
    </div>
</template>

<script>
    import Stock from './Stock.vue';
    export default {
        name: "stocks",
        components: {
            Stock
        },
        computed: {
            stocks() {
                return this.$store.getters.stocks;
            }
        },
    }
</script>

<style scoped>

</style>