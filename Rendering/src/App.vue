<script>
export default {
  data() {
    return {
      isDay: true,
      cartProducts: [
        { id: 1, name: 'Smartphone', price: 499.99, quantity: 2 },
        { id: 2, name: 'Laptop', price: 999.99, quantity: 1 },
        { id: 3, name: 'Headphones', price: 79.99, quantity: 3 },
        { id: 4, name: 'Tablet', price: 299.99, quantity: 2 },
      ],
    };
  },
  methods: {
    onDayChange() {
      this.isDay = !this.isDay;
    },
  },
};
</script>

<template>
  <h1>Hello world</h1>
  <h2 v-if="isDay">
    ☀️ It's sunny outside!
  </h2>
  <h2 v-else>
    🌑 It's dark outside!
  </h2>

  <template v-if="isDay">
    <p>
      🎉 Welcome to My Awesome Page 🎉
    </p>
    <span>
      👋 Hello there! This is a cool Vue.js example.
    </span>
  </template>

  <p v-else>
    Click the button above to reveal the exciting content! 😄
  </p>

  <button @click="onDayChange">
    Toggle time
  </button>

  <h2 v-show="!isDay">
    ☀️ THIS SHOULD BE HIDDEN IT'S A DAY ☀️
  </h2>
  <h2>My products</h2>
  <ul>
    <li v-for="(product, idx) in cartProducts" :key="`product-${idx}`">
      {{ product.name }}
    </li>
  </ul>
</template>
