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
  { id: 2234, color: 'green' },
  { id: 2235, color: 'blue' },
];

const sizes = ['S', 'M', 'L', 'XL'];

const description = ref('A pair of warm, fuzzy socks');
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <!-- image goes here -->
        <img
          :src="image"
          alt="socks blue"
        />
        <img
          :src="image2"
          alt="socks blue"
        />
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p>{{ description }}</p>
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
        >
          {{ variant.color }}
        </div>
        <ul>
          <li v-for="size in sizes">{{ size }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
