<template>
    <div id="app">
        <nav-bar></nav-bar>
                
        <div class="product">
            <left-column />            
            <center-column />
            <right-column />
        </div>
    </div>
</template>

<script>
    import NavBar from "./components/NavBar.vue";
    import LeftColumn from './components/LeftColumn.vue';
    import CenterColumn from './components/CenterColumn.vue';
    import RightColumn from './components/RightColumn.vue';
    import { mapState, mapActions } from 'vuex';

    export default {
        name: "App",
        components: {
            CenterColumn, LeftColumn, RightColumn, NavBar
        },
        data() {
            return {};
        },
        computed: {
            ...mapState(['product'])
        },
        methods: {
            ...mapActions(['productSelected', 'imageSelected'])
        },
        created() {
            this.productSelected({ 
                id: this.product.models[0].id,
                name: this.product.models[0].name,
                color: this.product.models[0].color,
                images: this.product.models[0].images,
                quantity: this.product.models[0].quantity,
                details: this.product.models[0].details
            });

            this.imageSelected({ 
                imagen: this.product.models[0].images[0], 
                index: 0 
            });
        },
    };
</script>

<style>
    body {
        margin: 0;
    }
    .product {
        padding: 20px;
        display: flex;
    }
</style>
