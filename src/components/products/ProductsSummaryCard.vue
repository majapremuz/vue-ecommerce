<template>
    <div class="card">
        <h3>
            {{ product.name }}
        </h3>
        <h5 class="price">Price: EUR {{ product.price.toFixed(2) }}</h5>
        <p class="description">Description: {{ description }}</p>
        <button class="view-product-button" @click="$emit('view-product', product)">View Product</button>
    </div>
</template>


<script>
  export default {
      props: ["product"],
      computed: {
          description() {
              return this.product.description.substring(0, 150)
          }
      }
  }
</script>


<style>
   .card {
       background-color: white;
       width: 70%;
       margin: 3rem;
       padding: 2rem;
       border-radius: 20px;
       box-shadow: 0px 0px 15px 1px #000000;
   }

   h3 {
       font-size: 2rem;
   } 

   .price {
       color: red;
   }

   .description {
       font-size: 0.8rem;
   }

   .view-product-button {
       background-color: rgb(191, 18, 29);
       color: white;
       border: none;
       cursor: pointer;
       font-size: 1.5rem;
       padding: 0.5rem;
   }
</style>

