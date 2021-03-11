<template>
    <div class="left-column">
        <div class="sidebar-img">
            <img
                v-for="(imagen, index) in selectProduct.images" 
                :key="index"
                :src="imagen" 
                :class="{ 'side-img': true, 'img-selected': index === selectImage.index }"
                @mouseenter="seleccionarImagen(imagen, index)"
            >                            
        </div>

        <img :src="selectImage.imagen" class="img" alt="">
    </div>    
</template>

<script>
    import { mapState, mapActions } from 'vuex';

    export default {
        name: 'left-column',
        data() {
            return {}
        },
        computed: {
            ...mapState(['selectProduct', 'selectImage'])
        },
        methods: {
            ...mapActions(['imageSelected']),

            seleccionarImagen (imagen, index) {
                this.imageSelected({ 
                    imagen, 
                    index 
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

    .left-column {
        padding-right: 20px;
        display: flex;
    }
    .sidebar-img {
        display: flex;
        flex-direction: column;
        margin-right: 25px;
    }
    .side-img {
        height: 42px;
        width: 42px;
        margin-bottom: 10px;
        border: 1px solid #a2a6ac;
    }
    .img {
        height: 500px;
        width: 500px;
    }
    .img-selected {
        border: 1px solid rgb(231, 118, 0);
    }
</style>