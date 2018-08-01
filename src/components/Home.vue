<template>
    <div>
        <h1>Trade or View your Portfolio</h1>
        <h6>You may save & Load your Data</h6>
        <h6>Click on 'End Day' to begin a new day</h6>
        <hr>
        <p>Your Funds: {{funds}}</p>
    </div>
</template>

<script>
    export default {
        name: "home",
        computed: {
            funds() {
                return this.$store.getters.funds;
            }
        },
    }
</script>

<style scoped>

</style>