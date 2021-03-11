<template>
    <div class="nav-bar">
            <div class="cart">
                <img src="../assets/cart.png"/>
                <span class="amount">{{ cartAmount }}</span>
                <span class="description">Cart</span>
            </div>
        </div>
</template>

<script>
    import { mapState } from 'vuex';

    export default {
        name: 'nav-bar',
        computed: {
            ...mapState(['cart']),
            
            cartAmount() {
                return this.cart.length;
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    body {
        margin: 0;
    }
    .nav-bar {
        position: relative;
        background-color: #232f3e;
        width: 100%;
        height: 50px;
    }
    .cart {
        position: absolute;
        right: 15px;
        bottom: 5px;
        color: white;
        font-weight: bold;
    }
    .cart > img {
        width: 38px;
        height: 26px;
    }
    .amount {
        color: #f08804;
        position: absolute;
        left: 10px;
        top: -5px;
        text-align: center;
        min-width: 25px;
    }
</style>