<script setup>
import { defineProps, defineEmits, inject } from 'vue'
const props = defineProps({
  carts: {
    type: Array,
    required: true,
  },
})

const emits = defineEmits(['remove-cart'])
const handleRemoveCart = (cart) => {
  emits('remove-cart', cart)
  console.log(cart)
  showNotification(`${cart.name}已移除購物車`)
}
const showNotification = inject('showNotification')
</script>
<template>
  <h2 class="mb-3">購物車</h2>
  <ul v-if="props.carts.length" class="list-group mb-3">
    <li
      v-for="cart in props.carts"
      :key="cart.id"
      class="list-group-item d-flex justify-content-between align-items-center"
    >
      <div>
        <h6 class="my-0">{{ cart.name }}</h6>
        <small class="text-muted">數量：{{ cart.quantity }}</small>
      </div>
      <div>
        <span class="text-muted">${{ cart.price * cart.quantity }}</span>
        <button class="btn btn-sm btn-outline-danger ms-2" @click="handleRemoveCart(cart)">
          移除
        </button>
      </div>
    </li>
  </ul>
  <p v-else>購物車目前沒有商品</p>
</template>
