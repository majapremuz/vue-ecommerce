<template>
    <div>
        <h1>Your cart</h1>

        <CartItemCard 
          v-for="product in products"
          :key="product.id"
          :product="product" />

        <CartSummaryPaymentCard />


    </div>
</template>


<script>
import CartItemCard from "../components/cart/cartItemCard.vue"
import CartSummaryPaymentCard from "../components/cart/CartSummaryPaymentCard.vue"

export default {
    components: {
       CartItemCard, CartSummaryPaymentCard
    },
    computed: {
        products() {
            return this.$store.getters.cartItems
        }
    }
}
</script>

