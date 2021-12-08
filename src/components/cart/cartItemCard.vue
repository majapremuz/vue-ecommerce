<template>
    <div class="cart-item-card">
        <div class="header">
            <h3>{{ product.name }}</h3>
            <h4>In cart: {{product.quantity }}</h4>
            <h4>Total Cost: {{item_cost.toFixed(2) }}</h4>
        </div>
        <p>{{ description }}</p>
    </div>
</template>


<script>
export default {
    props: ["product"],
    computed: {
        description() {
            return this.product.description.substring(0, 120)
        },
        item_cost() {
            return this.product.price * this.product.quantity
        }
    }
}
</script>

<style>
.cart-item-card {
    width: 50%;
    background-color: white;
    margin: 5rem auto;
    padding: 1rem;
    border-radius: 20px;
    box-shadow: 0px 0px 10px 1px #000000;
}

.header {
    display: flex;
    justify-content: space-around;
    flex-direction: column;
}
</style>
