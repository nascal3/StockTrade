<template>
    <nav class="navbar navbar-default">
        <div class="container-fluid">
            <!-- Brand and toggle get grouped for better mobile display -->
            <div class="navbar-header">
                <router-link to="/" class="navbar-brand">Stock Trader</router-link>
            </div>

            <!-- Collect the nav links, forms, and other content for toggling -->
            <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
                <ul class="nav navbar-nav">
                    <router-link to="/portfolio" active-class="active" tag="li"><a>Portfolio</a></router-link>
                    <router-link to="/stocks" active-class="active" tag="li"><a>Stocks</a></router-link>
                </ul>
                <ul class="nav navbar-nav navbar-right">
                    <li><a href="#" @click="endDay">End Day</a></li>
                    <strong class="navbar-text navbar-right">Funds: {{funds | currency}} </strong>
                    <li class="dropdown" @click="isDropDownOpen=!isDropDownOpen" :class="{open: isDropDownOpen}">
                        <a href="#"
                           class="dropdown-toggle"
                           data-toggle="dropdown"
                           role="button" aria-haspopup="true"
                           aria-expanded="false">Save & Load<span class="caret"></span></a>
                        <ul class="dropdown-menu">
                            <li><a href="#" @click="saveData">Save data</a></li>
                            <li><a href="#" @click="getData">Load data</a></li>
                        </ul>
                    </li>
                </ul>
            </div><!-- /.navbar-collapse -->
        </div><!-- /.container-fluid -->
    </nav>
</template>

<script>
    import {mapActions} from 'vuex';
    export default {
        name: "header",
        data() {
            return {
                isDropDownOpen: false
            }
        },
        computed: {
            funds() {
                return this.$store.getters.funds;
            }
        },
        methods: {
            ...mapActions([
                'randomizedStocks',
                'loadData'
        ]),
            endDay() {
                this.randomizedStocks();
            },
            saveData() {
                const data = {
                    funds: this.$store.getters.funds,
                    stockPortfolio: this.$store.getters.stockPortfolio,
                    stocks: this.$store.getters.stocks
                };
                this.$http.put('data.json', data);
            },
            getData() {
                this.loadData();
            }
        }

    }
</script>

<style scoped>

</style>