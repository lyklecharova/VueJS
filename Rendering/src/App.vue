<script>
export default {
  data() {
    return {
      isDay: true,
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
</template>
