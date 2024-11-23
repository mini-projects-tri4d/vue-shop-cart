<template>
    <div class="card">
        <div class="card-header bg-primary text-white">
            Kosár
        </div>
        <div class="card-body">
            <div v-if="cart.length === 0" class="text-center py-3">
                A kosár üres
            </div>
            <div v-else>
                <div v-for="item in cart" :key="item.id" class="mb-3 border-bottom pb-2">
                    <div class="d-flex justify-content-between align-items-center">
                        <span>{{ item.name }}</span>
                        <div class="btn-group">
                            <button class="btn btn-sm btn-outline-secondary" @click="$emit('decrease-quantity', item)">-</button>
                            <span class="btn btn-sm">{{ item.quantity }}</span>
                            <button class="btn btn-sm btn-outline-secondary" @click="$emit('increase-quantity', item)">+</button>
                        </div>
                    </div>
                    <div class="d-flex justify-content-between align-items-center mt-2">
                        <span>{{ formatPrice(item.price * item.quantity) }} Ft</span>
                        <button class="btn btn-sm btn-danger" @click="$emit('remove-from-cart', item)">Törlés</button>
                    </div>
                </div>
                <div class="mt-3 pt-3 border-top">
                    <strong>Összesen: {{ formatPrice(totalPrice) }} Ft</strong>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ShoppingCart',
    props: {
        cart: {
            type: Array,
            required: true
        }
    },
    computed: {
        totalPrice() {
            return this.cart.reduce((total, item) => total + (item.price * item.quantity), 0)
        }
    },
    methods: {
        formatPrice(price) {
            return price.toLocaleString()
        }
    }
}
</script>