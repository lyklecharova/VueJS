<script>
export default {
  data() {
    return {
      numberOfClicks: 10,
      dynamic: [{
        button: {
          id: 99,
        },
      }],
    };
  },
  methods: {
    increment() {
      this.numberOfClicks += 1;
    },
    decrement() {
      this.numberOfClicks -= 1;
    },
    changeButtonId() {
      this.dynamic[0].button.id = Date.now();
    },
  },
};
</script>

<template>
  <h1 class="myTitle">
    Hello World
  </h1>
  <h2
    class="btnClicks"
    :class="[
      {
        green: numberOfClicks > 20,
      },
      `clicks-${numberOfClicks}`,
    ]"
  >
    the button was clicked
    {{ numberOfClicks }}
    number of times!
  </h2>

  <div class="btnWrapper">
    <button @click="increment">
      increment
    </button>
    <button @click="decrement">
      decrement
    </button>
  </div>
  <button :id="dynamic[0].button.id" @click="changeButtonId">
    Dynamic ID button: {{ dynamic[0].button.id }}
  </button>
</template>

<style scoped>
.myTitle{
  color: red;
}
.btnWrapper{
  margin-bottom: 2rem;
}
.btnClicks{
  color: lightsalmon;
}
.btnClicks.green{
  color: green;
}
.btnGreen{
  color:green;
}
</style>
