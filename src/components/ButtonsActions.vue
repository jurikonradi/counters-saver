<template>
  <div class="flex">
    <button type="button" @click="increaseNumber">Increase</button>
    <button type="button" @click="decreaseNumber">Decrease</button>
  </div>
</template>

<script>
export default {
  name: "ButtonsActions",
  methods: {
    increaseNumber() {
      this.$emit("increaseNumber");
    },
    decreaseNumber() {
      this.$emit("decreaseNumber");
    },
  },
};
</script>

<style lang="sass">
@import "./CounterForm.sass"
</style>