<template>
    <div class="center-column">
        <div class="details">
            <h1>{{ product.name }}</h1>
            
            <hr/>

            <span :class="['stock', cmpClase ]"> {{ cmpMensaje }} </span>

            <span>Modelo: <b>{{ selectProduct.name }}</b></span>

            <div class="colors">
                <span
                    v-for="modelo in product.models" 
                    @click="seleccionarProducto(modelo)"
                    :key="modelo.id" 
                    :class="{ 'color-box': true, 'color-selected': modelo.id === selectProduct.id }"
                    :style="{ backgroundColor: modelo.color }"
                    :title="modelo.name">
                </span>
            </div>

            <ul class="details">
                <li v-for="(modelo, index) in selectProduct.details" :key="index">{{ modelo }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
    import { mapState, mapActions } from 'vuex';

    export default {
        name: 'center-column',
        data() { 
            return {}
        },
        computed: {
            ...mapState(['product', 'selectProduct']),

            cmpMensaje () {
                return (this.selectProduct.quantity <= 0 ? 'Sin Existencia': (this.selectProduct.quantity > 0 && this.selectProduct.quantity < 50 ? 'Por Agotarse' : 'En Stock'));
            },

            cmpClase (){
                return (this.selectProduct.quantity <= 0 ? 'out-of-stock': (this.selectProduct.quantity > 0 && this.selectProduct.quantity < 50 ? 'low-stock' : 'in-stock'));
            }
        },
        methods: {
            ...mapActions(['productSelected', 'imageSelected']),

            seleccionarProducto (modelo) {
                this.productSelected({ 
                    id: modelo.id,
                    name: modelo.name,
                    color: modelo.color,
                    images: modelo.images,
                    quantity: modelo.quantity,
                    details: modelo.details
                });

                this.imageSelected({ 
                    imagen: modelo.images[0], 
                    index: 0 
                });
            },
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    body {
        margin: 0;
    }
    .center-column {
        width: 760px;
        display: flex;
        flex-direction: column;
    }
    .details {
        display: flex;
        flex-direction: column;
        padding-left: 15px;
    }
    hr {
        margin-left: 0;
        margin-right: 0;
    }
    .stock {
        font-size: 25px;
        padding-bottom: 20px;
    }
    .in-stock {
        color: #007600;
    }
    .low-stock {
        color: #e77600;
    }
    .out-of-stock {
        color: #B12704;
    }
    .colors {
        display: flex
    }
    .color-box {
        margin: 10px 10px 0 0;
        border-radius: 3px;
        height: 36px;
        width: 36px;
    }
    .color-selected {
        height: 34px;
        width: 34px;
        border: 2px solid rgb(231, 118, 0);
    }    
</style>