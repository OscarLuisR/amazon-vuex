<template>
    <div class="right-column">
        <button 
            :disabled="selectProduct.quantity <= 0"
            :class="cmpHabilitaBoton"
            @click="addToCart">Add To Cart
        </button>
    </div>
</template>

<script>
    import { mapState, mapActions } from 'vuex';

    export default {
        name: 'right-column',
        data() {
            return {}
        },
        computed: {
            ...mapState(['selectProduct']),
            
            cmpHabilitaBoton(){
                return (this.selectProduct.quantity > 0 ? 'add-to-cart' : 'button-disable')
            }
        },
        methods: {
            ...mapActions(['addToCart']),

            addToCart() {
                this.addToCart();
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    body {
        margin: 0;
    }    
    .right-column {
        padding-left: 20px;
        display: flex;
    }
    .add-to-cart {
        background: linear-gradient(to bottom,#f7dfa5,#f0c14b);
        border-color: #a88734 #9c7e31 #846a29;
        border-radius: 3px;
        color: #111;
        width: 237px;
        height: 31px;
    }
    .add-to-cart:hover {
        border-color: #a88734 #9c7e31 #846a29;
        background: linear-gradient(to bottom,#f5d78e,#eeb933);
    }
    .button-disable {
        color: -internal-light-dark(rgba(16, 16, 16, 0.3), white);
        background-color: -internal-light-dark(rgba(239, 239, 239, 0.3), rgba(19, 1, 1, 0.3));
        border-color: -internal-light-dark(rgba(118, 118, 118, 0.3), rgba(195, 195, 195, 0.3));
        border-radius: 3px;
        width: 237px;
        height: 31px;
    }
</style>