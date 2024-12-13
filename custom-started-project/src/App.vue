<script>
export default {
  data() {
    return {
      numberOfClicks: 0,
    };
  },
  methods: {
    increment() {
      this.numberOfClicks += 1;
    },
    decrement() {
      this.numberOfClicks -= 1;
    },
  },
};
</script>

<template>
  <h1 class="myTitle">
    Hello World
  </h1>
  <h2>
    the button was clicked
    {{ numberOfClicks }}
    number of times!
  </h2>

  <button @click="increment">
    increment
  </button>
  <button @click="decrement">
    decrement
  </button>
</template>

<style>
.myTitle{
  color: red;
}
</style>
