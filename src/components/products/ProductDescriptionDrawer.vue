<template>
    <div class="drawer-background" :class="{show: active}" @click="$emit('close-product-drawer')">
    </div>

    <div class="drawer" :class="{show: active}">
        <div class="drawer-close" @click="$emit('close-product-drawer')">
            X
        </div>

        <div v-if="product" class="product-details">
            <h3 class="text-center"> {{ product.name }} </h3>
            <p class="description"> {{ product.description }} </p>
            <h3 class="text-center">EUR {{ product.price.toFixed(2) }}</h3>

            <div class="cart-total" v-if="product_total">
                <h3>In cart</h3>
                <h4> {{ product_total }}</h4>
            </div>

            <div class="button-container">
                <button class="remove" @click="removeFromCart()">Remove</button>
                <button class="add" @click="addToCart()">Add</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["product", "active"],
    methods: {
      addToCart() {
          this.$store.commit("addToCart", this.product)
      },
      removeFromCart() {
          this.$store.commit("removeFromCart", this.product)
      }
    },
    computed: {
        product_total() {
            return this.$store.getters.productQuantity(this.product)
        }
    }
}
</script>

<style>
 .drawer-background {
     background-color: rgba(85, 193, 255, 0.712);
     width: 100%;
     height: 100vh;
     position: fixed;
     left: 0;
     top: 0;
     z-index: 100;
     display: none;
     transition: display .5s;
 }

 .drawer-background.show {
     display: block;
 }

 .drawer {
     width: 95vw;
     height: 100vh;
     background-color: white;
     position: fixed;
     top: 0;
     left: -105vw;
     padding: 1rem;
     transition: left .5s;
     z-index: 101;
     overflow-y: scroll;
 }

 .drawer.show {
     left: 0;
 }

 .drawer-close {
     font-size: 1.5rem;
     padding: 0.3rem;
     border-radius: 20px;
     right: 10px;
     width: 15px;
     float: right;
     cursor: pointer;
 }

  .drawer-close:hover {
      background-color: lightgray;
  }

  .product-details {
      display: flex;
      justify-content: center;
      flex-direction: column;
  }

  p.description {
      padding: 1rem;
      line-height: 1rem;
  }

   .remove {
          width: 150px;
          border: none;
          padding: 10px;
          border-radius: 5px;
          margin: 0 3px 50px 5px;
          cursor: pointer;
      }

      .add {
          width: 150px;
          border: none;
          padding: 10px;
          border-radius: 5px;
          margin: 0 3px 50px 5px;
          cursor: pointer;
      }

@media screen and (max-width: 600px) {
    .drawer {
        width: 450px;
    }
}

</style>
