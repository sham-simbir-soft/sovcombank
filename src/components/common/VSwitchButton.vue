<template>
  <div
    class="switch"
    :class="{ switch__btn_active: active }"
    @click="$emit('click')"
  >
    <img v-if="!active" class="switch__icon" src="../../assets/plus.svg" />
    <img v-else class="switch__icon" src="../../assets/cancel.svg" />
    <slot>Текст</slot>
  </div>
</template>

<script>
export default {
  name: "VSwitchButton",
  props: {
    active: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
.switch {
  display: flex;
  align-items: center;
  color: #506981;
  margin-left: 20px;
  cursor: pointer;
}

.switch__btn_active {
  color: #adb9c4;
}

.switch__icon {
  width: 18px;
  height: 18px;
  margin-right: 10px;
}
</style>
