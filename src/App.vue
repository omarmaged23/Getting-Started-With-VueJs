<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'

const cart = ref([])
const premium = ref(true)

const incrementCart = (id) => {
  cart.value.push(id)
}

const decrementCart = () => {
  if(cart.value.length > 0)
    cart.value.pop()
}

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart.length }})</div>
  <ProductDisplay :premium="premium" @add-to-cart="incrementCart" @remove-from-cart="decrementCart"></ProductDisplay>
</template>