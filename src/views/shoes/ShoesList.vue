<template>
    <div>
        <h1>Hi</h1>
        <ul>
            <li v-for="product in products"
                v-bind:key="product.productId">{{product.description}}</li>
        </ul>

    </div>
</template>
¨
<script>
    import axios from 'axios';
  export default {
    mounted() {
      this.fetchProducts()
    },
    data: ()  => ({
      products: [{productId: 1, description: 'Helo'},{productId: 2, description: 'Bøf'}]
    }),
    methods: {
        fetchProducts() {

          axios.get('https://shoeshop.azurewebsites.net/api/products')
            .then((data) => {
              this.products = data.data;

            });
        }
    }
  };
</script>
