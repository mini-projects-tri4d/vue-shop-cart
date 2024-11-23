<template>
    <div class="card h-100">
        <div class="card-img-container">
            <img :src="product.image" class="card-img-top product-image" :alt="product.name">
        </div>
        <div class="card-body d-flex flex-column">
            <h5 class="card-title">{{ product.name }} ({{ product.packaging }})</h5>
            <p class="card-text">{{ formatPrice(product.price) }} Ft</p>
            <button class="btn btn-primary mt-auto" @click="$emit('add-to-cart', product)">
                Kosárba
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductCard',
    props: {
        product: {
            type: Object,
            required: true
        }
    },
    methods: {
        formatPrice(price) {
            return price.toLocaleString()
        }
    }
}
</script>

<style scoped>
.card-img-container {
    position: relative;
    width: 100%;
    padding-top: 100%;
    overflow: hidden;
}

.product-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: contain;
    padding: 1rem;
}

.card {
    transition: transform 0.2s;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
}

.card-body {
    padding: 1.25rem;
}

.card-title {
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
}

.card-text {
    font-size: 1.2rem;
    font-weight: bold;
    color: #2c3e50;
}

.btn-primary {
    width: 100%;
}
</style>
