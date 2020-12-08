<template>
  <div class="form">
    <button class="button-plus" action="button" @click="addForm">+</button>
    <CounterForm
      v-for="item in formsAll"
      v-bind:key="item.id"
      v-bind:childNumber="item.id"
      v-on:getValue="setValue"
    />
    <div class=".main-container">
      <button class="save" type="button" @click="saveInput">Save</button>
      <button class="restore" type="button" @click="restoreInput">
        Restore
      </button>
    </div>
  </div>
</template>

<script>
import CounterForm from "./CounterForm.vue";

export default {
  name: "ManyForms",
  data() {
    return {
      formsAll: [
        {
          id: 0,
          inputValue: undefined,
          savedValue: undefined,
          restoredValue: undefined,
        },
      ],
      childNumber: undefined,
    };
  },
  methods: {
    addForm() {
      let newItem = {
        id: this.formsAll.length,
        inputValue: undefined,
        savedValue: undefined,
        restoredValue: undefined,
      };
      this.formsAll.push({ newItem });
      console.log(this.formsAll);
    },
    setValue(value) {
      this.formsAll[this.id].inputValue = value;
      console.log("setValue: ", value);
    },
    saveInput() {
      this.formsAll.forEach((element) => {
        element.restoredValue = element.savedValue;
        element.savedValue = element.inputValue;
        console.log(
          "restoredValue:",
          element.restoredValue,
          ", savedValue:",
          element.savedValue
        );
      });
    },
    restoreInput() {
      this.formsAll.forEach((element) => {
        element.inputValue = element.restoredValue;
        console.log(
          "restoredValue:",
          element.restoredValue,
          ", savedValue:",
          element.savedValue
        );
      });
    },
  },
  components: {
    CounterForm,
  },
};
</script>

<style lang="sass" scoped>
@import './ManyForms.sass'
</style>
