<template>
    <div>
        <Stock v-for="stock in stocks" :stock="stock"></Stock>
    </div>
</template>

<script>
    import Stock from './Stock.vue';
    export default {
        name: "stocks",
        data() {
            return {
                stocks : [
                    { id: 1, name: 'BMW', price: 110},
                    { id: 2, name: 'Google', price: 200},
                    { id: 3, name: 'Apple', price: 250},
                    { id: 4, name: 'Twitter', price: 8},
                ]
            }
        },
        components: {
            Stock
        }
    }
</script>

<style scoped>

</style>