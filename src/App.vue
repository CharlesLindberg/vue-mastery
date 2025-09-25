<script setup>
import { ref } from 'vue';
import socksGreen from './assets/images/socks_green.jpeg';
import socksBlue from './assets/images/socks_blue.jpeg';

const product = ref('Socks');
const image = ref(socksGreen);
const image2 = ref(socksBlue);
const inStock = ref(true);
const inventory = ref(3);
const onSale = ref(false);

const details = ['50% cotton', '30% wool', '20% polyester'];

const variants = [
  { id: 2234, color: 'green', image: socksGreen },
  { id: 2235, color: 'blue', image: socksBlue },
];

const sizes = ['S', 'M', 'L', 'XL'];

const description = ref('A pair of warm, fuzzy socks');

const cart = ref(0);
const addToCart = () => (cart.value += 1);
const removeFromCart = () => (cart.value -= 1);

const updateImage = (variantImage) => {
  image.value = variantImage;
};
</script>

<template>
  <div class="nav-bar"></div>
  <div class="cart">{{ cart }}</div>

  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <!-- image goes here -->
        <img
          :src="image"
          alt="socks blue"
        />
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <!-- <p>{{ description }}</p> -->
        <p v-if="inventory > 10">In Stock</p>
        <p v-else-if="inventory <= 19 && inventory > 0">Almost sold out</p>
        <p v-else>Out of Stock</p>
        <p v-if="onSale">On Sale</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div
          v-for="variant in variants"
          :key="variant.id"
          @mouseover="updateImage(variant.image)"
        >
          {{ variant.color }}
        </div>
        <button
          class="button"
          v-on:click="addToCart"
        >
          Add to Cart
        </button>
        <button
          class="button"
          @click="removeFromCart"
        >
          -
        </button>
        <ul>
          <li v-for="size in sizes">{{ size }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
