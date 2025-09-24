<script setup>
import { ref } from 'vue';
import socksGreen from './assets/images/socks_green.jpeg';
import socksBlue from './assets/images/socks_blue.jpeg';

const product = ref('Socks');
const image = ref(socksGreen);
const image2 = ref(socksBlue);

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
      </div>
    </div>
  </div>
</template>
