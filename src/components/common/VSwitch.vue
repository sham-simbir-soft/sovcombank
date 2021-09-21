<template>
  <div class="switch">
    <span :class="['switch__value', { switch__value_active: isSwitch }]">
      <slot name="left">Значение слева</slot>
    </span>

    <div
      :class="['switch-btn', { 'switch-btn_on': isSwitch }]"
      @click="onSwitch()"
    />

    <span :class="['switch__value', { switch__value_active: !isSwitch }]">
      <slot name="right">Значение справа</slot>
    </span>
  </div>
</template>

<script>
export default {
  name: "VSwitch",
  model: {
    prop: "value",
    event: "change",
  },
  props: {
    value: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      isSwitch: false,
    };
  },
  methods: {
    onSwitch() {
      this.isSwitch = !this.isSwitch;

      if (this.isSwitch) this.$emit("change", "name");
      if (!this.isSwitch) this.$emit("change", "all");
    },
  },
};
</script>

<style scoped>
.switch {
  display: flex;
  align-items: center;
}

.switch__value {
  color: #adb9c4;
}

.switch__value_active {
  color: #506981;
  border-bottom: 1px dotted #506981;
}

.switch-btn {
  display: inline-block;
  width: 40px;
  height: 22px;
  margin: 0px 13px;
  border-radius: 15px;
  background: #5e9969;
  cursor: pointer;
  position: relative;
  transition-duration: 300ms;
}
.switch-btn::after {
  content: "";
  height: 18px;
  width: 18px;
  border-radius: 17px;
  background: #fff;
  top: 2px;
  left: 3px;
  transition-duration: 300ms;
  position: absolute;
  z-index: 1;
}

.switch-btn_on::after {
  left: 20px;
}
</style>
