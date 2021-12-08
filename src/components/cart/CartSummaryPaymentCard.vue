<template>
    <div class="cart-item-card">
        <h3>Cart Total: EUR {{ cart_total.toFixed(2) }}</h3>

        <form>
        <label for="first-name">First Name</label>
        <input type="text" id="first-name" required>
        <br>
        <label for="last-name">Last Name</label>
        <input type="text" id="last-name" required>
        <br>
        <label for="full-address">Full address</label>
        <input type="text" id="address" required>
        <br>
        <label for="email">Email</label>
        <input type="text" id="email" required>
        <br>   
        <label for="card-number">Card number</label>
        <input type="text" id="card-number" required>
        <br> 
        <button class="view-product-button">Pay</button>
        </form>

    </div>
</template>

<script>
  export default {
      computed: {
          cart_total() {
              return this.$store.getters.cartTotal
          }
      }
  }
</script>

<style>
form {
    display: flex;
    justify-content: center;
    flex-direction: column;
    background-color: rgb(186, 220, 236);
    padding: 1rem;
}

input {
    border-radius: 5px;
    padding: 0.5rem;
    width: 50%;
    margin: auto;
    border: 1px solid rgb(51, 51, 51);
}
</style>

