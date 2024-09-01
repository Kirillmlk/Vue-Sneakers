<script setup>
import CartItem from "./CartItem.vue";
import { inject } from "vue";

const { cart, addToCart, removeFromCart } = inject('cart');
</script>

<template>
    <div class="flex flex-col flex-1 gap-4 justify-between" v-auto-animate>
        <CartItem
            v-for="item in cart"
            :key="item.id"
            :title="item.title"
            :imageUrl="item.imageUrl"
            :price="item.price"
            @removeFromCart="removeFromCart(item)"
        />
    </div>
</template>
