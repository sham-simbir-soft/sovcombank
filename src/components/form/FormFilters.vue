<template>
  <div class="filters">
    <div v-if="switchFilters === 'all'" class="filters__select-group">
      <v-select
        class="filters__select"
        v-model="form.city"
        :array="cityList"
        select-first
      />
      <v-select
        class="filters__select"
        v-model="form.purpose"
        :array="purposeList"
      />
      <v-select class="filters__select" v-model="form.type" :array="typeList" />
    </div>

    <v-input
      v-else-if="switchFilters === 'name'"
      class="filters__input"
      v-model="form.name"
      placeholder="Введите название объекта (бизнес-центра, торгового центра, новостройки, логопарка)"
      input-first
    />

    <input
      class="filters__submit"
      type="submit"
      value="Найти"
      @click.prevent="onSubmit()"
    />
  </div>
</template>

<script>
import VSelect from "@/components/common/VSelect.vue";
import VInput from "@/components/common/VInput.vue";

export default {
  name: "FormFilters",
  components: {
    VSelect,
    VInput,
  },
  props: {
    form: {
      type: Object,
    },
    switchFilters: {
      type: String,
      default: "all",
    },
  },
  data() {
    return {
      cityList: ["Москва", "Самара", "Казань"],
      purposeList: ["Купить", "Продать"],
      typeList: ["Офис", "Квартира", "Дом"],
    };
  },
  methods: {
    onSubmit() {
      this.$emit("sendForm");
    },
  },
};
</script>

<style lang="scss" scoped>
.filters {
  display: flex;

  @media (max-width: 700px) {
    flex-direction: column;
  }
}

.filters__select-group {
  display: flex;
  flex: 1;

  @media (max-width: 700px) {
    flex-direction: column;
  }
}

.filters__select {
  flex: 1;
  margin-left: 1px;

  @media (max-width: 700px) {
    margin-left: 0px;
    margin-top: 1px;
    background: #ffffff;
  }
}

.filters__input {
  flex: 1;

  @media (max-width: 700px) {
    border-radius: 0;
  }
}

.filters__submit {
  display: flex;
  align-items: center;
  justify-content: center;

  flex: 0.2;
  min-height: 44px;
  font-size: 16px;
  color: #ffffff;
  background: #5e9969;

  border-radius: 0px 3px 3px 0px;
  outline: none;
  border: none;
  cursor: pointer;

  @media (max-width: 700px) {
    border-radius: 0;
  }
}
</style>
