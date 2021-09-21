<template>
  <div class="select">
    <select
      class="select__field"
      :class="[{ 'select-first': selectFirst }, { 'select-last': selectLast }]"
      :style="{ background }"
      :value="value"
      @change="onSelect($event.target.value)"
    >
      <option v-for="(item, index) in array" :key="index">{{ item }}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "VSelect",
  model: {
    prop: "value",
    event: "change",
  },
  props: {
    value: {
      type: String,
      default: "",
    },
    array: {
      type: Array,
    },
    selectFirst: {
      type: Boolean,
      default: false,
    },
    selectLast: {
      type: Boolean,
      default: false,
    },
    background: {
      type: String,
      default: "#ffffff",
    },
  },
  methods: {
    onSelect(event) {
      this.$emit("change", event);
    },
  },
};
</script>

<style lang="scss" scoped>
.select {
  position: relative;
}

.select__field {
  display: flex;
  align-items: center;
  padding: 0px 20px;

  width: 100%;
  min-height: 44px;
  border: none;
  outline: none;
  appearance: none;
  font-size: 16px;
  cursor: pointer;
}

.select:after {
  content: "";
  display: block;
  border-style: solid;
  border-width: 6px 5px 0 5px;
  border-color: #506981 transparent transparent transparent;
  pointer-events: none;
  position: absolute;
  top: 50%;
  right: 1rem;
  z-index: 1;
  margin-top: -3px;
}

.select-first {
  border-radius: 3px 0px 0px 3px;
}

.select-last {
  border-radius: 0px 3px 3px 0px;
}
</style>
