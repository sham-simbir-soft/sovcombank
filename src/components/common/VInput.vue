<template>
  <input
    class="input"
    :class="{ 'input-first': inputFirst }"
    type="text"
    :placeholder="placeholder"
    @input="onInput($event.target.value)"
  />
</template>

<script>
export default {
  name: "VInput",
  model: {
    prop: "value",
    event: "change",
  },
  props: {
    value: {
      type: [String, Number],
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
    inputFirst: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    onInput(event) {
      this.$emit("change", event);
    },
  },
};
</script>

<style lang="scss" scoped>
.input {
  width: 100%;
  min-height: 44px;
  padding: 0px 20px;
  border: none;
  border-right: none;
  outline: none;
  font-size: 16px;
}

.input-first {
  border-radius: 3px 0px 0px 3px;
}
</style>
