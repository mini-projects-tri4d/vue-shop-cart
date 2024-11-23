<template>
    <nav class="navbar navbar-dark bg-dark mb-4">
        <div class="container">
            <span class="navbar-brand">Vue Webshop</span>
            <button class="btn btn-outline-light" @click="showCart = !showCart">
                Kosár ({{ cartItemCount }})
            </button>
        </div>
    </nav>

    <div class="container">
        <div class="row">
            <div :class="{'col-md-8': showCart, 'col-12': !showCart}">
                <div class="row">
                    <div v-for="product in products" :key="product.id" class="col-md-4 mb-4">
                        <ProductCard 
                            :product="product"
                            @add-to-cart="addToCart"
                        />
                    </div>
                </div>
            </div>

            <div v-if="showCart" class="col-md-4">
                <ShoppingCart
                    :cart="cart"
                    @remove-from-cart="removeFromCart"
                    @increase-quantity="increaseQuantity"
                    @decrease-quantity="decreaseQuantity"
                />
            </div>
        </div>
    </div>
</template>

<script>
import { ref, computed } from 'vue'
import ProductCard from './components/ProductCard.vue'
import ShoppingCart from './components/ShoppingCart.vue'
import { products } from './data/products'
import './assets/style.css'

export default {
    name: 'App',
    components: {
        ProductCard,
        ShoppingCart
    },
    setup() {
        const showCart = ref(false)
        const cart = ref([])

        const cartItemCount = computed(() => {
            return cart.value.reduce((total, item) => total + item.quantity, 0)
        })

        const addToCart = (product) => {
            const existingItem = cart.value.find(item => item.id === product.id)
            if (existingItem) {
                existingItem.quantity++
            } else {
                cart.value.push({
                    ...product,
                    quantity: 1
                })
            }
            showCart.value = true
        }

        const removeFromCart = (item) => {
            const index = cart.value.indexOf(item)
            if (index > -1) {
                cart.value.splice(index, 1)
            }
        }

        const increaseQuantity = (item) => {
            item.quantity++
        }

        const decreaseQuantity = (item) => {
            if (item.quantity > 1) {
                item.quantity--
            } else {
                removeFromCart(item)
            }
        }

        return {
            showCart,
            cart,
            products,
            cartItemCount,
            addToCart,
            removeFromCart,
            increaseQuantity,
            decreaseQuantity
        }
    }
}
</script>