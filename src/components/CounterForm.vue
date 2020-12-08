<template>
  <form class="form-container">
    <div class="main-container">
      <input
        class="input-area"
        type="text"
        name="number-input"
        id="number-input"
        placeholder="Enter number"
        v-model="toParent.inputValue"
        @input="onlyNumbers"
        v-on:change="sendToParent"
      />
      <ButtonsActions
        @increaseNumber="increaseNumber"
        @decreaseNumber="decreaseNumber"
      />
    </div>
  </form>
</template>

<script>
import ButtonsActions from "@/components/ButtonsActions";

export default {
  name: "CounterForm",
  data() {
    return {
      toParent: {
        inputValue: undefined,
        childNumber: this.childNumber,
      },
    };
  },
  props: {
    childNumber: {
      type: Number,
    },
  },
  methods: {
    sendToParent() {
      this.$emit("getValue", this.toParent.inputValue);
      console.log("sendToParent: ", this.toParent.inputValue);
    },
    onlyNumbers() {
      this.toParent.inputValue = this.toParent.inputValue.replace(
        /[^0-9]/g,
        ""
      );
    },
    increaseNumber() {
      this.toParent.inputValue++;
      this.$emit("getValue", this.toParent.inputValue);
      console.log(this.toParent.childNumber + ": " + this.toParent.inputValue);
    },
    decreaseNumber() {
      this.toParent.inputValue--;
      this.$emit("getValue", this.toParent.inputValue);
    },
  },
  components: { ButtonsActions },
};
</script>

<style lang="sass">
@import "./CounterForm.sass"
</style>