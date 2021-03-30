<template>
  <div class="home">
    <h1 class="text-primary"><fa icon="shopping-cart" />Shopping Cart</h1>
    <Curr />
    <CustomAlert />
    <Product />
  </div>
</template>

<script>
 import Curr from '@/components/Curr'
 import CustomAlert from '@/components/CustomAlert'
 import Product from '@/components/Product'

export default {
  name: 'Home',

  data: function() {
    return {
      max: 50,
      cart: [],
      displayCart: false,
      products: []
    }
  },
  components: {
    Curr,
    CustomAlert,
    Product
  },
  created() {
    fetch('https://hplussport.com/api/products/order/price')
      .then(response => response.json())
      .then(data => {
        this.products = data
      })
  },
  computed: {
    filteredProducts() {
      return this.products.filter(item => item.price < this.max)
    },
    cartTotal() {
      return this.cart.reduce((inc, item) => Number(item.price) + inc, 0)
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product)
      if (this.cartTotal >= 100) {
        this.salesBtn = 'btn-danger'
      }
    }
  }
}
</script>
