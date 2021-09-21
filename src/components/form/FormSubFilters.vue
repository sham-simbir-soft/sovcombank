<template>
  <div class="filters">
    <div v-if="switchSubFilters === 'price'" class="filters__row">
      <v-input
        class="filters__input"
        v-model="form.startPrice"
        placeholder="От"
        input-first
      />

      <v-input
        class="filters__input"
        v-model="form.endPrice"
        placeholder="До"
      />

      <v-select
        class="filters__select"
        v-model="form.period"
        :array="periodArray"
        select-last
        background="#e6f2fe"
      />

      <div
        class="filters__btn filters__btn-price"
        @click="$emit('change', 'metric')"
      >
        Добавить метраж
      </div>
    </div>

    <div v-else-if="switchSubFilters === 'metric'" class="filters__row">
      <div
        class="filters__btn filters__btn-metric"
        @click="$emit('change', 'price')"
      >
        Добавить цену
      </div>

      <v-input
        class="filters__input"
        v-model="form.startSquare"
        placeholder="От"
        input-first
      />

      <v-input
        class="filters__input"
        v-model="form.endSquare"
        placeholder="До"
      />

      <div class="filters__metric">
        м²
      </div>
    </div>
  </div>
</template>

<script>
import VSelect from "@/components/common/VSelect.vue";
import VInput from "@/components/common/VInput.vue";

export default {
  name: "FormSubFilters",
  components: {
    VSelect,
    VInput,
  },
  props: {
    form: {
      type: Object,
    },
    switchSubFilters: {
      type: [String, Number],
      default: "",
    },
  },
  data() {
    return {
      periodArray: ["₽/месяц", "₽/сутки"],
    };
  },
};
</script>

<style lang="scss" scoped>
.filters__row {
  display: flex;
  align-items: center;

  @media (max-width: 700px) {
    flex-direction: column;
  }
}

.filters__input {
  flex: 1;
  margin-left: 1px;
  background: #e6f2fe;

  @media (max-width: 700px) {
    margin-left: 0;
    margin-top: 1px;
    border-radius: 0;
  }
}

.filters__select {
  flex: 1;
  margin-left: 1px;

  @media (max-width: 700px) {
    width: 100%;
    margin-left: 0;
    margin-top: 1px;
    background: #e6f2fe;
  }
}

.filters__btn {
  display: flex;
  align-items: center;
  justify-content: center;

  min-height: 44px;
  border: 1px solid #506981;
  border-radius: 3px;
  font-size: 16px;
  cursor: pointer;

  @media (max-width: 700px) {
    width: 100%;
    margin-left: 0;
    margin-top: 20px;
  }
}

.filters__btn-price {
  flex: 2;
  margin-left: 20px;

  @media (max-width: 700px) {
    width: 100%;
    margin-left: 0;
    margin-top: 20px;
  }
}

.filters__btn-metric {
  flex: 4.5;
  margin-right: 20px;

  @media (max-width: 700px) {
    width: 100%;
    margin-right: 0;
    margin-bottom: 20px;
  }
}

.filters__metric {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 54px;
  height: 44px;
  background: #c2e3f2;
  border-radius: 0px 3px 3px 0px;

   @media (max-width: 700px) {
    width: 100%;
    margin-left: 0;
    border-radius: 0;
  }
}
</style>
