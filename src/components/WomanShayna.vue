<template>
    <!-- Women Banner Section Begin -->
    <section class="women-banner spad">
        <div class="container-fluid">
            <div class="row">
                <div class="col-lg-12 mt-5" v-if="products.length > 0">
                    <carousel class="product-slider" :dots="false" :autoplay="true" :nav="false">
                        <div class="product-item" v-for="product in products" :key="product.id">
                            <div class="pi-pic">
                                <img :src="product.galleries[0].photo" alt="" />
                                <ul>
                                    <li class="w-icon active" @click="saveKeranjang(productDetails.id, productDetails.name, productDetails.price, productDetails.galleries[0].photo)">
                                        <router-link :to="'/product/' + product.id"><i class="icon_bag_alt"></i></router-link>
                                    </li>
                                    <li class="quick-view"><router-link :to="'/product/' + product.id">+ Quick View</router-link></li>
                                </ul>
                            </div>
                            <div class="pi-text">
                                <div class="catagory-name">{{ product.type }}</div>
                                <a href="#">
                                    <h5>{{ product.name }}</h5>
                                </a>
                                <div class="product-price">
                                    {{ product.price }}
                                    <span>$35.00</span>
                                </div>
                            </div>
                        </div>
                    </carousel>
                </div>
                <div class="col-lg-12 mt-2" v-else>
                    <p>Product terbaru belum tersedia saat ini</p>
                </div>
            </div>
        </div>
    </section>
    <!-- Women Banner Section End -->
</template>
<script>
import carousel from 'vue-owl-carousel'
import axios from 'axios'
export default {
    name: "WomanShayna",
    components: {
        carousel
    },
    data() {
        return {
            products: [],
            keranjangUser: []
        }
    },
    mounted() {
        axios
            .get("http://shayna-backend.belajarkoding.com/api/products")
            .then(res => (this.products = res.data.data.data))
            .catch(err => console.log(err))

    },
    methods: {
        saveKeranjang(idProduct, nameProduct, priceProduct, photoProduct) {
            let productStored = {
                "id": idProduct,
                "name": nameProduct,
                "price": priceProduct,
                "photo": photoProduct
            }
            this.keranjangUser.push(productStored);
            const parsed = JSON.stringify(this.keranjangUser);
            localStorage.setItem('keranjangUser', parsed);
        }
    },
}
</script>

<style scoped>
.product-item {
    margin-right: 25px;
}
</style>